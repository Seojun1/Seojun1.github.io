---
title: "첫 오픈소스 기여"
date: 2026-07-12 15:40:00 +0900
categories: [Github]
tags: [Git, 오픈소스, Contributors]
---

# 첫 오픈소스 기여


말년 휴가를 나와서 하루종일 코딩만 구주장창 하다가 문득 오픈소스를 찾아보게 되었다.
누군가가 만든 Big Project에 나의 코드를 기여할 수 있다는 것이 매우 재밌어보여서 즉흥적으로 OpenSource Contribution에 대해 찾아봤다 !

## 기여 방법

기본적인 Git의 사용법(Fork, Pull, Branch 등)만 알고있다면 큰 걸림돌 없이 진행할 수 있었다.
대략적인 순서는 아래와 같다.

1. 기여하고 싶은 프로젝트를 찾아서 Fork 하기
2. Fork한 Repo를 Clone해서 작업을 위한 새로운 branch 만들기(feature)
3. 작업이 끝나면 내 작업 환경에 Push하기
4. PR 보내기

## 첫 PR

나는 **rio** 라는 파이썬으로 웹앱을 만들 수 있는 오픈소스를 택했다.
rio에는 웹을 만들 수 있는 여러 컴포넌트가 존재하는데 그 중 하나의 컴포넌트를 조금 건들여보고자 했다.

그래서 진행한 작업은 rio의 달력 컴포넌트의 세부 기능을 새롭게 추가하는 작업이었다. 뭐 사용자 입장에서 그렇게까지 필요한 요소는 아니지만 그래도 있으면 좋으니 바로 로직을 짜보았다.

오픈소스다보니 코드를 하나하나 분석해서 어떤 방식으로 동작 하는지를 파악해야했는데 이 과정에서 시간을 제일 많이 쏟았던 것 같다ㅠㅜ

---

어찌저찌 분석한 결과, 컴포넌트에 대한 선언은 calendar.py, style은 calendar.scss, 속성 및 데이터 전달은 calendar.ts에서 작동되고 있었다. 

```python
# calendar.py

    value: date

    _: dataclasses.KW_ONLY

    is_sensitive: bool = True
    mark_weekends: bool = False
    on_change: rio.EventHandler[DateChangeEvent] = None

    def _custom_serialize_(self) -> JsonDoc:
        return {
            "selectedYear": self.value.year,
            "selectedMonth": self.value.month,
            "selectedDay": self.value.day,
            "monthNamesLong": self.session._month_names_long,
            "dayNamesLong": self.session._day_names_long,
            "firstDayOfWeek": self.session._first_day_of_week,
            "markWeekends": self.mark_weekends,
        }

```

markWeekends라는 속성을 넣기 위해 bool 변수 선언과 *custom_serialize* 함수에 할당해주었다.

```tsx
// calendar.ts

updateElement(
        deltaState: DeltaState<CalendarState>,
        context: ComponentStatesUpdateContext
    ): void {
        super.updateElement(deltaState, context);

        // Toggle class based on the `mark_weekends` property from Python backend
        if (deltaState.markWeekends !== undefined) {
            if (deltaState.markWeekends) {
                this.element.classList.add("rio-calendar-mark-weekends");
            } else {
                this.element.classList.remove("rio-calendar-mark-weekends");
            }
        }
```

mark_weekends의 속성 값인 True, False 두 가지 경우에 대한 데이터 처리를 해주었고 이에 대한 Docstring 
또한 작성해주었다.

```scss
// calendar.scss

.rio-calendar.rio-calendar-mark-weekends {
    .rio-calendar-grid > .rio-calendar-day-name:nth-child(7n + 1) {
        color: #ff4d4f !important;
    }
    .rio-calendar-grid > .rio-calendar-day-name:nth-child(7n) {
        color: #1890ff !important;
    }

    .rio-calendar-grid
        > .rio-calendar-day:nth-child(7n + 1):not(.rio-calendar-selected-day) {
        color: #ff4d4f !important;
    }
    .rio-calendar-grid
        > .rio-calendar-day:nth-child(7n):not(.rio-calendar-selected-day) {
        color: #1890ff !important;
    }
}
```

Python으로 mark_weekends 속성을 새로 생성하고, ts를 통해 사용자의 사용 여부를 결정한다. 
사용자가 입력한 mark_weekends의 속성 값이 True가 들어왔을 경우 변경될 style도 scss에 넣어주었다.

마지막으로 npm을 사용해서 제대로 동작하는지 확인 후, 새로운 Branch에 commit - push를 하고나서 
드디어 PR을 보냈다 !

![image.png](/assets/images/firstOpenSource/image.png)

## 마치며

오픈소스를 만들어낸 쪽에서 내가 보낸 PR을 보고 기능 & 코드를 검토한다. 
그리고 나서 Merge를 할건지 아님 그냥 Closed를 할건지를 결정하는데 그냥 바로 Closed 하는 곳도 많다고 
한다 ..

머 일단 기다려봐야징