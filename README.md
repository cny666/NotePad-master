# 期中实验NotePad
## 姓名:陈乃耀  学号：116052017058
### 时间戳
#### 实验结果
![时间戳](https://github.com/cny666/NotePad-master/blob/master/app/src/main/res/drawable/1.png)  
#### 先将当前系统时间转换成yyyy-MM-dd格式
#### SimpleDateFormat ModifyDate = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
#### String modifydate = ModifyDate.format(System.currentTimeMillis());
#### 将获得的时间插入
#### values.put(NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE, modifydate);
#### 将时间戳显示出来
#### String[] dataColumns = { NotePad.Notes.COLUMN_NAME_TITLE ,NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE} ;
#### int[] viewIDs = { android.R.id.text1,  android.R.id.text2};
#### 在notelist_item添加一个id为text2的TextView
### 搜索
#### 实验结果
![实验结果](https://github.com/cny666/NotePad-master/blob/master/app/src/main/res/drawable/2.png)  
#### 实验结果
![实验结果](https://github.com/cny666/NotePad-master/blob/master/app/src/main/res/drawable/3.png)
#### 添加一个note_serchlist布局包括SerchView和ListView
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">
    <SearchView
        android:id="@+id/serch1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:iconifiedByDefault="false"
        android:queryHint="@string/hint" />

    <ListView
        android:id="@android:id/list"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />
</LinearLayout>


#### 对SerchView进行监听
                String selection = NotePad.Notes.COLUMN_NAME_TITLE + " Like ? ";
                String[] selectionArgs = { "%" + newText + "%" };
                Cursor cursor = managedQuery(
                        getIntent().getData(),            // Use the default content URI for the provider.
                        PROJECTION,                       // Return the note ID and title for each note. and modifcation date
                        selection,
                        selectionArgs,
                        NotePad.Notes.DEFAULT_SORT_ORDER
                );
                String[] serchdata1 = { NotePad.Notes.COLUMN_NAME_TITLE, NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE };
                int[] viewIDs = { android.R.id.text1 ,android.R.id.text2 };
                SimpleCursorAdapter adapter
                        = new SimpleCursorAdapter(
                        getApplicationContext(),
                        R.layout.noteslist_item,
                        cursor,
                        serchdata1,
                        viewIDs
                );
                setListAdapter(adapter);
                return true;
####
