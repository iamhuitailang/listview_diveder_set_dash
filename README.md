# listview_diveder_set_dash
listview 分割线 设置虚线

1

解决方案A：setLayerType(View.LAYER_TYPE_SOFTWARE, null)

保持如本案例中第一步和第二步的代码原封不动，只需要在Java代码中做一次判断：

[java] view plain copy
LinearLayout dashLine=(LinearLayout) findViewById(R.id.dashLine);  
        if(android.os.Build.VERSION.SDK_INT >= android.os.Build.VERSION_CODES.HONEYCOMB) {  
            dashLine.setLayerType(View.LAYER_TYPE_SOFTWARE, null);  
        }  
当Android在3.0及以上版本时候setLayerType(View.LAYER_TYPE_SOFTWARE, null);即可顺利画出虚线分割线。

2 

其实就是解决方案A的Java代码转移到xml中做配置，保持本案例中第一步代码原封不动，仅仅在第二步的代码中增加设置一个属性android:layerType="software" 改进成这样：


[html] view plain copy
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
    xmlns:tools="http://schemas.android.com/tools"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    android:background="@android:color/white"  
    android:orientation="vertical" >  
  
    <TextView  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:text="csdn zhangphil" />  
  
    <LinearLayout  
        android:id="@+id/dashLine"  
        android:layout_width="match_parent"  
        android:layout_height="2dip"  
        android:background="@drawable/dash_line"  
        android:layerType="software"  
        android:orientation="horizontal" />  
  
    <TextView  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:text="csdn zhangphil" />  
  
</LinearLayout>  

3
解决方案C：修改AndroidManifest.xml中的application属性，设置：android:hardwareAccelerated="false"。

4
动态添加
mListView.setDivider(getResources().getDrawable(android.R.drawable.arrow_down_float));  
