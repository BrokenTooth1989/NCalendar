# NCalendar








一款安卓日历，月视图，周视图滑动切换，时间从1901-01-01到2099-12-31

支持自定义日期区间

支持农历，节假日，指示圆点，默认视图，周的第一天设置等

支持单一月日历、周日历设置默认选中和默认不选中


## 效果图

![](https://github.com/yannecer/NCalendar/blob/master/app/new_.gif)

## 下载demo：
https://github.com/yannecer/NCalendar/blob/master/app/app-debug.apk

## 使用方法


#### 布局文件

```
miui9 和 钉钉日历

     android:id="@+id/miui9Calendar"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:calendarHeight="300dp">

        <android.support.v7.widget.RecyclerView
            android:id="@+id/recyclerView"
            android:layout_width="match_parent"
            android:layout_height="match_parent" />

    </com.necer.calendar.Miui9Calendar>
    
 miui10（不完美）
    
    <com.necer.calendar.Miui10Calendar
        android:id="@+id/miui10Calendar"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:bgChildColor="#F5f5f5">

        <android.support.v4.widget.NestedScrollView
            android:layout_width="match_parent"
            android:layout_height="match_parent">
        </android.support.v4.widget.NestedScrollView>
        
    </com.necer.calendar.Miui10Calendar>


华为 和 365日历

    <com.necer.calendar.EmuiCalendar
        android:id="@+id/emuiCalendar"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:bgCalendarColor="#ffffff"
        app:holidayColor="#F29B38"
        >

        <android.support.v4.widget.NestedScrollView
            android:layout_width="match_parent"
            android:layout_height="match_parent">
            
        </android.support.v4.widget.NestedScrollView>
    </com.necer.calendar.EmuiCalendar>

```
#### 注意


```NCalendar```内部需要一个实现了```NestedScrollingChild```的子类，```RecyclerView```，```NestedScrollView```都可以。

单个的周日历和月日历可以设置默认不选中（即是点击才选中，不点击不选中），但是月周切换必须每页都选中，这样才能体现出月周日期无缝切换的特点，
该日历不支持月周切换的不选中设置



### 交流群

技术交流QQ群：127278900<br/>请添加备注：github、NCalendar、安卓....





### 主要Api


##### 1、监听
```
nCalendar.setOnCalendarChangedListener(new OnCalendarChangedListener() {
            @Override
            public void onCalendarDateChanged(NDate date) {
               //日历回调 NDate包含公历、农历、节气、节假日、闰年等信息
            }
               
            @Override
            public void onCalendarStateChanged(boolean isMonthSate) {
               //日历状态回调， 月->周 isMonthSate返回false ，反之返回true   
            }
        });
```

##### 2、跳转日期
```
参数为 yyyy-MM-dd 格式的日期

ncalendar.jumpDate("2017-12-31"); 
```
##### 3、回到今天
```
ncalendar.toToday(); 
```

##### 4、日历切换，月-->周  周-->月
```
ncalendar.toWeek();
ncalendar.toMonth();
```
##### 5、上一月、下一月、上一周、下一周
```
ncalendar.toNextPager();
ncalendar.toLastPager();

```

##### 6、添加指示圆点
```
List<String> pointList = Arrays.asList("2018-10-01", "2018-11-19", "2018-11-20", "2018-05-23", "2019-01-01");
ncalendar.setPointList(list);

```
##### 7、默认视图 
```
app:defaultCalendar="week"  默认周视图
app:defaultCalendar="month"  默认月视图
```



### 支持的属性：
## Attributes属性（banner布局文件中调用）
|Attributes|forma|describe
|---|---|---|
|solarTextColor| color|公历日期的颜色
|lunarTextColor| color|农历日期的颜色
|solarHolidayTextColor| color|公历节假日的颜色
|lunarHolidayTextColor| color|农历节假日的颜色
|solarTermTextColor| color|节气颜色
|hintColor| color|不是本月公历日期的颜色
|selectCircleColor| color|选中圈的颜色
|holidayColor|color| 法定节休息日颜色
|workdayColor|color| 法定节调休工作日颜色
|bgCalendarColor|color| 日历的背景
|bgChildColor|color| 日历包含子view的背景
|pointColor| color |小圆点的颜色
|todaySolarTextColor| color|今天不选中的颜色
|selectCircleRadius| dimension | 选中圈的半径

|solarTextSize| dimension|公历日期字体大小
|lunarTextSize| dimension|农历日期字体大小
|lunarDistance| dimension|农历日期到公历字体的距离
|holidayTextSize| dimension|法定节假日字体的大小
|holidayDistance| dimension |法定节假日到公历的距离
|pointDistance| dimension |小圆点到公历的距离
|hollowCircleStroke| dimension |空心圆的宽度
|calendarHeight| dimension |日历的高度



|duration|integer| 日历自动滑动的时间
|isShowLunar| boolean |是否显示农历
|isShowHoliday|boolean| 是否显示法定节假日
|isDefaultSelect|boolean| 是否默认选中（只对单个月日历或者周日历有效）

|defaultCalendar|enum| 默认视图 week 或者 month
|pointLocation|enum| 指示点的文职 up（在公历的上方） 或者 down（在公历的下方） 默认是up
|firstDayOfWeek|enum| 一周开始的星期天还是星期一 sunday 或者 monday 默认是sunday
|holidayLocation|enum| 法定节假日相对公历日期的位置 top_right（右上方）、top_left（左上方）、bottom_right（右下方）、bottom_left（左下方）



