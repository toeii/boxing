# boxing改
因boxing长期没人维护，为了解决以前项目留下的问题，便新建分支对[boxing](https://github.com/bilibili/boxing)进行升级和修复。

## Gradle
Step 1. 

```XML
    allprojects {
        repositories {
            ...
            maven { url 'https://jitpack.io' }
        }
    }
```
Step 2. 

```XML
    dependencies {
       implementation 'com.github.toeii:boxing:v1.0.5'
    }
```

注意：如果没有引入ucrop的话，需要引入ucrop

```XML
    dependencies {
	...
        implementation('com.yalantis:ucrop:2.2.0') {
		exclude group: 'com.android.support'
		exclude group: 'com.squareup.okio'
		exclude group: 'com.squareup.okhttp3'
	}
    }
```

## 更新说明
### v1.0.6
---
- 适配Android 11
- 修复圆形裁剪结果图为矩形的问题

### v1.0.5
---
- 修复Android 10设备上崩溃的BUG
- 新增圆形裁剪模式

```java
	BoxingCropOption cropOption = new BoxingCropOption(destUri);
	cropOption.isCircleMode(true);//圆形裁剪模式
	BoxingConfig singleCropImgConfig = new BoxingConfig(BoxingConfig.Mode.SINGLE_IMG).withCropOption(cropOption)
		.withMediaPlaceHolderRes(R.drawable.ic_boxing_default_image);
	Boxing.of(singleCropImgConfig).withIntent(this, BoxingActivity.class).start(this, REQUEST_CODE);
```

## 项目原地址

[bilibili boxing](https://github.com/bilibili/boxing)
