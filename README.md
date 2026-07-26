## 掌上重邮使用文档

---

## 模拟数据

1. 在文件`mockSchedule.json`中模拟课程信息的数据
2. 在uesEffect中使用`fetch("/mockSchedule.json")`进行网络请求获得数据

-----

## ActivityDetail.js

说明：负责活动详情界面

##### 主要函数：ActivityDetail() 参数：activity, onClose, onEdit

| 参数     | 说明                                           |
| -------- | ---------------------------------------------- |
| activity | 接受活动的信息                                 |
| onClose  | 一个关闭活动详情页面的函数                     |
| onEdit   | 接收函数handleEditActivity()，打开修改活动界面 |

| 返回内容 | 说明                           |
| -------- | ------------------------------ |
| 修改按钮 | 点击调用onEdit打开修改活动界面 |
| 活动信息 | 活动的标题、时间、内容         |
| 遮罩     | 点击遮罩推出详情界面           |

---

## TimePicker.js

说明：添加活动的选择时间的时间选择器

##### 主要函数：TimePicker()   参数：visible, selectedTimes, onAddSlot, onRemoveSlot, onClose

| 参数          | 说明                                            |
| ------------- | ----------------------------------------------- |
| visible       | 用于控制TimePicker组件的显示与隐藏              |
| selectedTimes | 已选的时间段                                    |
| onAddSlot     | 接收函数handleAddTimeSlot()，添加时间段         |
| onRemoveSlot  | 接收函数handleRemoveTimeSlot(),删除所选的时间段 |
| onClose       | 接收函数handleCloseWeeksPicker()，关闭当前界面  |

| 返回内容                                | 说明                                      |
| --------------------------------------- | ----------------------------------------- |
| selected-times                          | 已选的时间段，selectedTimes               |
| Picker                                  | 供选择的时间段                            |
| add-slot-btn                            | 按钮，点击调用函数handleAdd()，添加时间段 |
| confirm-btn                             | 按钮，点击关闭周次选择的界面              |
| 另：该组件引入了包react-mobile-picker。 |                                           |

---

## AddActivityModal.js

说明：负责添加和修改活动的界面和功能

##### 主要函数：AddActivityModal（） 

##### 参数：visible, step, title, content, time,selectedWeeks, selectedTimes,weeksPickerVisible, timesPickerVisible,setActivityTitle, setActivityContent, setActivityTime,onNext, onFinish,onWeekToggle, onOpenWeeksPicker, onCloseWeeksPicker, onAddSlot, onRemoveSlot, onOpenTimesPicker, onCloseTimesPicker.

| 参数               | 说明                                               |
| ------------------ | -------------------------------------------------- |
| visible            | 用于控制 `AddActivityModal` 组件的显示与隐藏       |
| step               | 表示添加活动的流程进行到第几项                     |
| title              | 表示活动标题                                       |
| selectedWeeks      | 表示已选的周次                                     |
| selectedTimes      | 表示已选的时间段                                   |
| weeksPickerVisible | 用于控制选择周次界面的显示与隐藏                   |
| timesPickerVisible | 用于控制TimePicker组件的显示与隐藏                 |
| setActivityTitle   | 用于更新活动标题                                   |
| setActivityContent | 用于更新活动内容                                   |
| setActivityTime    | 用于更新活动时间                                   |
| onNext             | 更新step来使流程进入下一项                         |
| onFinish           | 接收函数handleFinish()，实现流程的最后确认         |
| onWeekToggle       | 接收函数handleWeekToggle(),切换周次选择            |
| onOpenWeeksPicker  | 接收函数handleOpenWeeksPicker(),打开周次选择面板   |
| onCloseWeeksPicker | 接收函数handleCloseWeeksPicker(),关闭周次选择面板  |
| onAddSlot          | 接收函数handleAddTimeSlot()，添加时间段            |
| onRemoveSlot       | 接收函数handleRemoveTimeSlot(),删除所选的时间段    |
| onOpenTimesPicker  | 接收函数handleOpenTimesPicker(),打开时间选择面板   |
| onCloseTimesPicker | 接收函数handleCloseTimesPicker(),关闭时间选择面板  |
| onSelectAll        | 接收函数handleSelectAllWeeks()，判断是否设为整学期 |

| 返回内容 | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| 页面一   | step-content 添加标题                                        |
| 1        | 一个`<input/>`存储标题                                       |
| 2        | preset-tags,提供的标题标签版块                               |
| 页面二   | step-content 添加具体内容                                    |
| 页面三   | step-content 选择时间段                                      |
| 1        | add-time-btn 两个{+}按钮，点击分别调用函数handleOpenWeeksPicker()打开周次选择面板，调用handleOpenTimesPicker()打开时间选择面板 |
| 2        | selected-weeks 一个显示已选周次的版块                        |
| 3        | selected-times-preview 一个显示已选的具体时间的版块          |
| 四       | nextBtn 一个控制流程进度的按钮                               |
| 五       | WeekPicker 周次选择面板                                      |
| 1        | week-picker-overlay 一个遮罩，点击调用函数handleCloseWeeksPicker()关闭面板 |
| 2        | week-tags 一个提供可选周次面板的版块                         |
| 3        | confirm-btn 一个确认选择周次的按钮，点击调用函数handleCloseWeeksPicker()关闭面板 |
| 4        | TimePicker 引入TimePicker.js组件，负责选择时间版块           |

---

## CourseDetail.js

说明：负责课程详情界面

##### 主要函数：CourseDetail 参数：course，onClose

| 参数    | 说明                                  |
| ------- | ------------------------------------- |
| course  | 表示选择的课程                        |
| onClose | 更新setSelectedCourse的状态，关闭界面 |

| 返回内容           | 说明                              |
| ------------------ | --------------------------------- |
| detail-drawer open | 详情页的版块                      |
| 1                  | 课程的名称、教室、教师            |
| 2                  | 一个`<ul>` 课程的周期、时间、类型 |
| detail-overlay     | 遮罩，点击关闭详情页              |

---

## ScheduleTable.js

说明：负责整个课表

##### 主要函数：ScheduleTable 

##### 参数： periods, weekdays, weekdayNames, courses, activities,dragActivityId, dragOverCell,setSelectedCourse, setSelectedActivity, handleDeleteActivity, scheduleMap,onCellClick, onDragStart, onDragOver, onDragEnter, onDragLeave, onDrop, currentWeek , onDragStartTouch, onDragMoveTouch, onDragEndTouch

| 参数                 | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| periods              | 一个由数字1到18组成的数组                                    |
| weekdays             | 一个由数字1到7组成的数组                                     |
| weekdayNames         | 一个数组，里面的元素为按顺序排列的{周n n日}                  |
| courses              | 表示课程                                                     |
| activities           | 表示活动                                                     |
| dragActivityld       | 表示拖拽的活动id                                             |
| dragOverCell         | 表示拖拽过程中手指或鼠标当前悬停的单元格坐标                 |
| setSelectedCourse    | 用来更新selectedCourse的状态                                 |
| setSelectedActivity  | 用来更新selectedActivity的状态                               |
| handleDeleteActivity | 接收函数handleDeleteActivity(),用来删除活动                  |
| scheduleMap          | 一个对象，外层键是星期数字（1-7），内层键是起始节次数字（1-12），值是对应的课程信息对象 |
| onCellClick          | 接收函数handleOpenAddActivity(),打开添加活动界面，重置之前的添加信息 |
| onDragStart          | 接收函数onDragStart()，在拖拽活动的开始阶段存入活动数据，设置仅允许移动 |
| onDragOver           | 接收函数onDragOver(),阻止浏览器的默认行为，设置拖拽时的鼠标光标为“移动”图标 |
| onDragEnter          | 接收函数onDragEnter(),拖拽进空单元格时更新dragOverCell的状态 |
| onDragLeave          | 接收函数onDragLeave(),防止快速划过或移到子元素时高亮意外闪烁，确保只有真正离开那个格子才取消高亮 |
| onDrop               | 接收函数onDrop(),处理拖拽的活动松手放置后的情况              |
| currentWeek          | 表示当前的周次                                               |
| onDragStartTouch     | 接收函数onDragStartTouch(),处理触摸移动开始时的事件          |
| onDragMoveTouch      | 接收函数onDragMoveTouch(),处理触摸移动中的事件               |
| onDragEndTouch       | 接收函数onDragEndTouch(),处理触摸移动结束后的事件            |

| 返回内容      | 说明                                                  |
| ------------- | ----------------------------------------------------- |
| 星期          | 遍历weekdayNames                                      |
| period-cell   | 节次列的数字                                          |
| course-cell   | 有课程的单元格，里面显示课程的名称、教室              |
| activity-cell | 有活动的单元格，里面显示活动的标题、内容、时间        |
| delete-icon   | 一个标签{x}，点击删除活动                             |
| empty-cell    | 空白单元格                                            |
| add-btn       | 一个标签{+}，鼠标悬停在空白格上时显示，表示可添加活动 |

---

## App,js

##### 定义的状态：

- open: 初始状态为false，控制课表的开关
- selectedCourse：初始状态为null，表示选中的课程
- selectedActivity：初始状态为null，表示选中的活动
- courses：初始状态为[]，表示所有的课程
- loading：初始状态为true，表示课表的加载状态
- activities：初始状态为[]，表示所有手动添加的活动
- activity：初始状态为false，控制添加活动界面的开关
- step：初始状态为1，控制添加活动的流程
- activityTitle：初始状态为’ ’，表示添加活动的活动标题
- activityContent：初始状态为‘ ’，表示添加活动的活动内容
- activityTime：初始状态为‘ ’，表示添加活动的活动时间
- currentCell：初始状态为null，表示用户点击的空单元格坐标
- weekOffset：初始状态为0，表示周偏移量
- dragActivityId：初始状态为null，表示拖拽的活动id
- dragOverCell：初始状态为null，表示拖拽过程中手指或鼠标当前悬停的单元格坐标
- selectedWeeks：初始状态为[]，表示已选的周次
- weeksPickerVisible：初始状态为false，用于控制选择周次界面的显示与隐藏
- selectedTimes：初始状态为[],表示已选的时间段
- timesPickerVisible：初始状态为false，用于控制选择时间段界面的显示与隐藏
- editingActivity：初始状态为null，表示正在被编辑的活动对象
- isDraggingTouch：初始状态为false，用于标记移动端是否已进入长按拖拽模式
- touchStartPos：初始状态为{ x: 0, y: 0 }，表示移动端触摸开始时活动的坐标

##### 日期的计算：

1. 选择2026.7.20为基准时间，通过周偏移量weekOffset来计算出课程的星期、日时间，并返回
2. 获取系统的当前时间，来表示目前的周次和星期
3. 通过计算当前周的首日月份和末日月份，来表示出当前周所处的月份

##### 冲突检测：

1. 定义finalWeek，表示添加活动最后确认的周次；定义slots，表示添加活动最后确认的时间段
2. 如果scheduleMap当前对应位置已有课程，则无法添加
3. 定义conflictActivity，判断和已添加的活动是否有冲突

##### 添加活动：

1.如果是正在修改活动的话，即`if(editingActivity)`时，更新原来的活动信息

2.如果不是的话，则是新建活动，从零开始填写活动信息

| 重要函数               | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| handleMoveActivity()   | 处理拖拽活动的事件，包括冲突、放置                           |
| onDragStartTouch()     | 处理触摸开始的事件，记录活动id和起始坐标，并清除之前的定时器，重新计时，通过触摸时间来确认是否拖拽 |
| onDragMoveTouch()      | 处理触摸移动时的事件，通过坐标获得经过的单元格的信息，决定是否高亮 |
| onDragEndTouch()       | 处理触摸结束后的事件，清除计时器，判断长短按，长按则时拖拽活动，短按则是打开活动详情，最后重置拖拽状态 |
| handleSelectAllWeeks() | 处理整学期的选择事件                                         |

| 返回内容              | 说明                             |
| --------------------- | -------------------------------- |
| toggle-button         | 控制课表开关的按钮               |
| currentWeek、monthStr | 表示当前课表的周次和月份         |
| current               | 一个按钮，功能为回到本周         |
| ScheduleTable         | 一个组件，负责整个课表的渲染     |
| CourseDetail          | 一个组件，负责课程详情页的渲染   |
| ActivityDetail        | 一个组件，负责活动详情页的渲染   |
| AddActivityModal      | 一个组件，负责添加活动界面的渲染 |
| last、next            | 两个按钮，用于左右切换课表       |



##                                   感谢阅读 

