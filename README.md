# (Deprecated) DraggedViewPager
## Deprecated
The project has been deprecared. Use [DragListView](https://github.com/woxblom/DragListView) instead, [woxblom](https://github.com/woxblom) has been working on it for serveral years and always reply issues in time.

---
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-DraggedViewPager-green.svg?style=flat)](https://android-arsenal.com/details/1/2164)

A View whose pages and items both can be dragged, looking like a ViewPager

<img src="https://github.com/yueban/DraggedViewPager/raw/master/DraggedViewPager.gif" width="300"  alt="Screenshot"/>

## Gradle
DraggedViewPager is avaiable in [JCenter](https://bintray.com/bintray/jcenter?filterByPkgName=DraggedViewPager)

**Gradle dependency:**
```gradle
compile 'com.bigfat.draggedviewpager:library:1.0.7'
```

## Usage
###  Quick Start
```xml
<!-- Define a ScrollView by id "@id/dvp_scroll_view" in your page layout -->
<ScrollView
    android:id="@id/dvp_scroll_view"
    android:layout_width="match_parent"
    android:layout_height="wrap_content" />
```

``` java
//init Controller
MDA_DraggedViewPagerController<T1 extends Page<T2>, T2> controller = new MDA_DraggedViewPagerController<>(List<T1> data,int pageLayoutRes, int itemLayoutRes) {
    @Override
    public void bindPageData(View pageView, int pageIndex) {
    //bind page data...
    }

    @Override
    public void bindItemData(View itemView, int pageIndex, int itemIndex) {
    //bind item data...
    }
};
//set Controller
draggedViewPager.setController(controller);
draggedViewPager.setItemMoveDelay(200);
draggedViewPager.setPageSwapDelay(400);
//draggedViewPager.setIsDragEnabled(false);//default is true
//...see sample for more detail
```

### Callback
``` java
draggedViewPager.setOnPageSelectedListener(new OnPageSelectedListener() {
    @Override
    public void onPageSelected(int pageIndex) {

    }
});

draggedViewPager.setDraggedViewPagerListener(new MDA_DraggedViewPagerListener() {
    @Override
    public void onDragStarted() {

    }

    @Override
    public void onDragEnded() {

    }

    @Override
    public void onPageSwapped(int firstPageIndex, int secondPageIndex) {

    }

    @Override
    public void onItemMoved(int oldPageIndex, int oldItemIndex, int newPageIndex, int newItemIndex) {

    }
});
```

### Setting
```java
draggedViewPager.setPageDragSetting(new PageDragSetting() {
    @Override
    public boolean canBeDragged(int pageIndex) {
        return false;
    }
    @Override
    public boolean canBeSwiped(int pageIndex) {
        return false;
    }
});
```

### Control DraggedViewPager
``` java
controller.swapPages(int firstIndex, int secondIndex);
controller.addPage(int pageIndex, Page<T> page);
controller.removePage(int pageIndex);
controller.addItem(int pageIndex, int itemIndex, T item);
controller.removeItem(int pageIndex, int itemIndex);
controller.updateItem(int pageIndex, int itemIndex, T item);
controller.moveItem(int oldPageIndex, int oldItemIndex, int newPageIndex, int newItemIndex)
```

powered by [mingdao](http://www.mingdao.com/home)

## License

    Copyright 2015 yueban

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
