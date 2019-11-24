# 手动创建一个 Activity

在 Android 中是视图与逻辑分离的, 一个  Activity 主要组成如下： 布局 、逻辑.

创建一个活动大概步骤：

*   1 先创建一个Activity类
*   2 定义布局文件,并在 Activity 中进行指定
*   3 在 AndroidManifest.xml 进行声明
*   4 通过 intent-filter 把它指定为主活动,才能正常使用 （main函数,这个就是应用程序的入口）

``` xml

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.activitytest">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">

        <!--
            1   .FristActivity 指定声明的活动，.FristActivity是 com.example.activitytest.FristActivity 的缩写
            2   主要是在 mainfest中已经指定了 package
            3   label 指定Activity的标题 （title）
            4   theme 指定其主题（样式）
        -->
        <activity
            android:name=".FristActivity"
            android:label="@string/title_activity_frist"
            android:theme="@style/AppTheme">

            <intent-filter>
                <!--行为-->
                <action android:name="android.intent.action.MAIN"></action>
                <!--类目-->
                <category android:name="android.intent.category.LAUNCHER"></category>
            </intent-filter>

        </activity>
    </application>

</manifest>


```

## 在活动中使用 Toast 组件

``` java
    // 获取页面中元素 （在前端可以理解为  getElementById(id)）
    Button button1 = (Button)  findViewById(R.id.button_1);
    // 设置事件监听器 （addEventListener(eventname, handler)）
    button1.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Toast.makeText(FristActivity.this, "You clicked Button1", Toast.LENGTH_SHORT).show();
        }
    });

```

## 在活动中使用 Menu

在 Android 中视图和逻辑分离的，一般如果需要添加页面元素都需要通过 xml 方式来添加, 那么菜单也不例外.
创建一个菜单的大概步骤,如下:

*   在 res 下创建一个 menu 文件夹, 这是一种约定, 项目所有菜单都可以放置在这个下面.

``` xml

<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/add_item"
        android:title="Add"
        />
    <item android:id="@+id/remove_item"
        android:title="Remove"
        />
</menu>

```

* 重写 onCreateOptionsMenu 方法

``` java
    // 故名思意, 创建菜单选项
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // getMenuInflater 有点类似 findViewById , 主要用来得到 MenuInflater 对象
        // inflate 方法指定当前活动的菜单
        getMenuInflater().inflate(R.menu.main, menu);
        return true;
    }

    // 前面只是创建菜单，如果想知道用户点击那个菜单，必须重写 onOptionsItemSelected 方法, on 一般可以理解为事件监听. 这种模式写过前端的应该特别熟悉, 想监听用户行为时必须通过事件来进行监听.
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        switch (item.getItemId()){
            case R.id.add_item :
                Toast.makeText(FristActivity.this, "You clicked Add", Toast.LENGTH_SHORT).show();
                break;
            case R.id.remove_item:
                Toast.makeText( FristActivity.this,  "You clicked remove", Toast.LENGTH_SHORT).show();
                break;
            default:
        }
        return true;
    }

```

* 销毁一个活动

一般而言活动是有声明周期的, 如果想手动去销毁某个活动的话, 可以通过 Activity 提供的 ``finish()`` 方法来做这个事

``` java

    button1.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            FristActivity.this.finish();
            // finish();
        }
    });

```
上面两种写法是等价的,后者是前者的简写. 这里其实就知道在 Android 中也就上下文的概念, 这种类似浏览器中全局对象 window, 只要你运行在我当前的上下文环境中,就可以访问当前上文中的属性、方法等等.


