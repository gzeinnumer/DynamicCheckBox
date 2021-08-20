<h1 align="center">
<img src="https://github.com/gzeinnumer/DynamicCheckBox/blob/master/preview/example1.jpg" width="300"/> <img src="https://github.com/gzeinnumer/DynamicCheckBox/blob/master/preview/example3.jpg" width="300"/>

</h1>

<h1 align="center">
  DynamicCheckBox - Easy CheckBox Dynamic
</h1>

<div align="center">
    <a><img src="https://img.shields.io/badge/Version-2.1.0-brightgreen.svg?style=flat"></a>
    <a><img src="https://img.shields.io/badge/ID-gzeinnumer-blue.svg?style=flat"></a>
    <a><img src="https://img.shields.io/badge/Java-Suport-green?logo=java&style=flat"></a>
    <a><img src="https://img.shields.io/badge/Kotlin-Suport-green?logo=kotlin&style=flat"></a>
    <a href="https://github.com/gzeinnumer"><img src="https://img.shields.io/github/followers/gzeinnumer?label=follow&style=social"></a>
    <br>
    <p>Simple way to use Dynamic CheckBox</p>
</div>

---
# Content List
* [Download](#download)
* [Feature List](#feature-list)
* [Usage](#usage)
* [Example Code/App](#example-codeapp)
* [Version](#version)
* [Contribution](#contribution)

---
# Download

Add maven `jitpack.io` and `dependencies` in `build.gradle (Project)` :
```gradle
// build.gradle project
allprojects {
  repositories {
    ...
    maven { url 'https://jitpack.io' }
  }
}

// build.gradle app/module
dependencies {
  ...
  implementation 'com.github.gzeinnumer:DynamicCheckBox:version'
}
```

---
# Feature List
- [x] [Dynamic CheckBox](#DynamicCheckBox)

---
# Usage

### DynamicCheckBox

- Widget on `xml`
```xml
<com.gzeinnumer.dc.DynamicCheckBox
    android:id="@+id/dc"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>
```

if you want to custom your `CheckBox` use `app:style="@style/checkBoxStyle"` on view, and make style on your `res->value->style.xml`
```xml
<resources xmlns:tools="http://schemas.android.com/tools">

    <style name="checkBoxStyle" parent="Base.Theme.AppCompat">
        <item name="android:textColor">#FFE500</item>
    </style>
</resources>
```
```xml
<com.gzeinnumer.dc.DynamicCheckBox
    ...
    app:orientationCheckBox="horizontal"
    app:style="@style/checkBoxStyle"/>
```

#
- **Content Item** there is 2 type list that you can sent to this `CheckBox`.

**Type 1**
```java
DynamicCheckBox dynamicCheckBox = findViewById(R.id.dc);

ArrayList<String> listString = new ArrayList<String>();
listString.add("Satu");
listString.add("Dua");
listString.add("Tiga");
listString.add("Empat");

dynamicCheckBox.setItemList(listString)
    .setOnCheckedChangeListener(new DynamicCheckBox.OnCheckedChangeListener<String>() {
        @Override
        public void onCheckedChanged(ArrayList<String> items) {
            for (int i=0; i<items.size(); i++){
                Log.d(TAG, "onCheckedChanged: "+items.get(i));
            }
        }

        @Override
        public void onCheckedShow(String clickedValue) {
            Log.d(TAG, "onCheckedShow: "+clickedValue);
        }
    });
```

**Type 2** for this type you should override function `toString()` in your `model pojo`
```java
public class ExampleModel {

    private int id;
    private String name;
    private String address;

    //constructor

    //getter
    //setter

    @Override
    public String toString() {
        return "ExampleModel{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", address='" + address + '\'' +
                '}';
    }
}
```
Use your own model and dont forget to declare your `model pojo` in `onCallBack`. Example `DynamicCheckBox.OnCheckedChangeListener<ExampleModel>`
```java
DynamicCheckBox dynamicCheckBox = findViewById(R.id.dc);

ArrayList<ExampleModel> listObject = new ArrayList<>();
listObject.add(new ExampleModel(1, "Zein", "Balbar"));
listObject.add(new ExampleModel(2, "Zein2", "Balbar2"));
listObject.add(new ExampleModel(3, "Zein3", "Balbar3"));
listObject.add(new ExampleModel(4, "Zein4", "Balbar4"));

dynamicCheckBox.setItemList(listObject)
    .setOnCheckedChangeListener(new DynamicCheckBox.OnCheckedChangeListener<ExampleModel>() {
        @Override
        public void onCheckedChanged(ArrayList<ExampleModel> items) {
            for (int i=0; i<items.size(); i++){
                Log.d(TAG, "onCheckedChanged: "+items.get(i).getName());
                Log.d(TAG, "onCheckedChanged: "+items.get(i).getAddress());
            }
        }

        @Override
        public void onCheckedShow(String clickedValue) {
            Log.d(TAG, "onCheckedShow: "+clickedValue);
        }
    });
```
#
Set `setSelectedItem(index)` use before `setItemList(list)`.
```java
dynamicCheckBox.setSelectedItem(1,2,3).setItemList(list). ...
//or
dynamicCheckBox.setSelectedItem(new ArrayList<Integer>()).setItemList(list). ...
```

#
**Preview** :

| <img src="https://github.com/gzeinnumer/DynamicCheckBox/blob/master/preview/example1.jpg"/>| <img src="https://github.com/gzeinnumer/DynamicCheckBox/blob/master/preview/example3.jpg"/> |
|:---|:---|
| Preview `Single Object`| Preview `Model Pojo`|

| <img src="https://github.com/gzeinnumer/DynamicCheckBox/blob/master/preview/example2.jpg"/> |
|:---|
| Output data `Single Object`|

| <img src="https://github.com/gzeinnumer/DynamicCheckBox/blob/master/preview/example4.jpg"/> |
|:---|
|  Output data `Model Pojo`|

---
# Example Code/App

**FullCode [MainActivity](https://github.com/gzeinnumer/DynamicCheckBox/blob/master/app/src/main/java/com/gzeinnumer/dynamiccheckbox/MainActivity.java) & [ExampleModel](https://github.com/gzeinnumer/DynamicCheckBox/blob/master/app/src/main/java/com/gzeinnumer/dynamiccheckbox/ExampleModel.java) & [XML](https://github.com/gzeinnumer/DynamicCheckBox/blob/master/app/src/main/res/layout/activity_main.xml)**

[Sample Code And App](https://github.com/gzeinnumer/MyLibDynamicCheckBoxExample)

---
# Version

- **1.0.3**
  - First Release
- **2.0.0**
  - Support SDK 16
- **2.0.1**
  - Bug Fixing
- **2.1.0**
  - `setSelectedItem()`

---
# Contribution

You can sent your constibution to `branch` `open-pull`.

---

```
Copyright 2020 M. Fadli Zein
```
