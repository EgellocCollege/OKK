[![](https://img.shields.io/jitpack/v/github/Zeuskartik/MediaSliderView?label=JitPack)](https://jitpack.io/#Zeuskartik/MediaSliderView)     [![Build status](https://ci.appveyor.com/api/projects/status/9l0ubq1ng77dpm3n?svg=true)](https://ci.appveyor.com/project/Zeuskartik/mediasliderview)  [![Maintainability](https://api.codeclimate.com/v1/badges/ddf05107edffa60b69e7/maintainability)](https://codeclimate.com/github/Zeuskartik/MediaSliderView/maintainability)    [![License](https://img.shields.io/badge/License-Apache%202.0-orange.svg)](https://opensource.org/licenses/Apache-2.0)    ![GitHub top language](https://img.shields.io/github/languages/top/Zeuskartik/MediaSliderView?color=Green&label=Java)     ![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/Zeuskartik/MediaSliderView?color=Green&label=Code%20Size)

![Repository Logo](https://res.cloudinary.com/kartiksaraf/image/upload/v1564513200/github_MediaSliderView/Media_Slider_View_jkapxa.png)

# MediaSliderView     

Sliding Gallery View with support for images and videos, for android applications (Androidx support enabled).


## Capabilities and Functionalities

MediaSliderView is a compact library for having a slideable/swipeable gallery view inside your android application, which supports both images and videos. MediaSliderView uses Glide (https://github.com/bumptech/glide) for images and exoplayer (https://github.com/google/ExoPlayer) for videos, under the hood, to render images and videos inside customviews which are handled by a viewpager to render a swipeable gallery with on demand view creation, updation and destruction. The libraray itself is highly customizable and the images in the gallery support pinch, zoom and panning capabilities and play/pause/restart support for videos.


## What's Included ?   

-Swipe left and right to navigate the gallery.      
-Fast and efficient image loading with Glide.       
-Exoplyer support for playing videos inside the gallery.       
-Supports Url's as well as local file paths.      
 (Note: android Uri's are not supported, only absolute file paths can be used).      
-Progress indicators for resource load progress.       
-Title for gallery view.    
-Navigation buttons on either sides to navigate through the gallery smoothly.    
-Resource count view(current/total).


## Supported MediaTypes    

**The gallery, at a given instance of time can host only one type of media content, either images or videos.**      

As of now for videos only **.mp4** file format is supported and for images **.jpeg** and **.png** file formats are supported.



## Download & Setup
Repository available on https://jitpack.io.  

1). Add the jitpack support to your project-level gradle file.

```Gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
```
2). Add the gradle dependency in the build.gradle file.  

Note: Replace Tag with the current version.

```Gradle
dependencies {
   implementation 'com.github.Zeuskartik:MediaSliderView:Tag' //eg.- implementation 'com.github.Zeuskartik:MediaSliderView:1.0'
}

```    


3). Add the necessary permissions (as per your use case), in your manifest.xml as follows - 

i. Internet (when using Url's)     
```
<uses-permission android:name="android.permission.INTERNET" />   
```     

ii. Read External Storage (when using local filepaths)
```
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
```    
Note: When using local filepaths, make sure to check permission at runtime to read external storage. Also, Uri's are not supported yet, the user needs to  provide absolute file path to the resource to be loaded.  


4). Create a new java class in your app/src/main/java/<com.yourpackagename> folder and extend 'MediaSliderActivity'.

```
public class SliderDemo extends MediaSliderActivity {


}
```   

5). Register this new class inside your manifest.xml (since this class extends an activity now).


6). Override the 'onCreate' method inside this java class.

```
public class SliderDemo extends MediaSliderActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        
    }
}
```    

7). Inside 'onCreate' call loadMediaSliderView() method of the 'MediaSliderActivity'    

The loadMediaSliderView() method takes the foolowing arguemnts-    

| Parameter            | Type              | Value           | Inference                                                                                                                                                        |
|----------------------|-------------------|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| mediaUrlList         | ArrayList<String> |                 | An Arraylist of String type containing  either URL's or local filepaths  or a combination of both  for a given media type(i.e. image or video)  in string format. |
| mediaType            | String            | "image"/"video" | Type of media the gallery will host,  either images or videos.                                                                                                   |
| isTitleVisible       | boolean           | true/false      | Specifies whether the title of the gallery  will be visible or not.                                                                                              |
| isMediaCountVisible  | boolean           | true/false      | Specifies whether the item count of the  gallery will be visible or not.                                                                                         |
| isNavigationVisible  | boolean           | true/false      | Specifies whether the left and right  navigation buttons will be visible or not.                                                                                 |
| title                | String            |                 | Title of the slider gallery view.                                                                                                                                |
| titleBackgroundColor | String            | Eg.-"#ffffff"   | Backgroundcolor of the title bar for the gallery. It only accepts hexadecimal color strings.                                                                     |
| titleTextColor       | String            | Eg.-"#000000"   | Text color of the gallery title. It only accepts hexadecimal color strings.                                                                                      |


## License

MediaSliderView is available under the Apache 2.0 License. See the LICENSE file for more info.
