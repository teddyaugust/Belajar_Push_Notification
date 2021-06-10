# Belajar_Push_Notification

PROYEK BELAJAR ANDROID STUDIO

Topik 			: Setting Firebase dan One Signal

Nama File 		: Belajar Push Notfication
Package 		: package com.belajar.pushnotification;


>> Buat New Project di Android Studio 
>> Punya Akun di One Signal : https://onesignal.com/ (USER : lcs@gmail.com P: nl2020)
>> Punya Akun di Firebase : https://firebase.google.com/ (USER : lcs@gmail.com P: nl2020)


===============================================
STEP 1 : BUAT APLIKASI ANDROID
===============================================


===============================================
STEP 2 : BUAT NEW APP DI ONE SIGNAL
===============================================
Sampai pada proses diminta : Firebase Server Key dan Firebase Sender ID.


===============================================
STEP 3 : BUKA KEMBALI PROJECT ANDROID
===============================================

>> Klik Menu :  TOOLS
>> Klik Sub Menu : Firebase
>> Di Window Firebase cari : Cloud Messaging
>> Klik : Set Up Firebase Cloud Messaging
>> Akan muncul window : Set Up Firebase Cloud Messaging
>> Step 1: Connect your app to Firebase. 		<<KLIK : CONNECT TO FIREBASE>>
>> 



===============================================
STEP 4 : BUKA FIREBASE WEBSITE
===============================================

>> Masuk ke Firebase Console
>> Buat Project : Belajar Push Notifications
>> Ikut 3 Stepnya
>> Setelah Project terbentuk, kini saatnya menambahkan Firebase ke Applikasi
>> Klik Logo "Android" pada "Get Started by adding Firebase to your app"
>> Muncul Window : Add Firebase to your Android Applikasi

>> Step 1 : Register App
Masukkan Android package name : com.belajar.pushnotification
Masukkan App nickname : Belajar Push Notification
SHA-1 (opsional) bisa diisi atau tidak
lalu Klik : Register app

>> Step 2 : Download Config file yaitu google-service.json
Masuk ke Android Studio
Copy file json tadi ke Mode Project lalu App
Setelah itu di halaman Firebase, klik Next

>> Step 3 : Add Firebase SDK
Ikuti arahan :

Pada build.gradle (Project) isinya :
====================================

// Top-level build file where you can add configuration options common to all sub-projects/modules.
buildscript {
    repositories {
        google()
        mavenCentral()
    }
    dependencies {
        classpath "com.android.tools.build:gradle:4.2.1"
        classpath 'com.google.gms:google-services:4.3.8'

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}

allprojects {
    repositories {
        google()
        mavenCentral()
        jcenter() // Warning: this repository is going to shut down soon
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}


Pada build.gradle (Module) isinya :
====================================


plugins {
    id 'com.android.application'
    id 'com.google.gms.google-services'
}

android {
    compileSdkVersion 30
    buildToolsVersion "30.0.3"

    defaultConfig {
        applicationId "com.belajar.pushnotification"
        minSdkVersion 19
        targetSdkVersion 30
        versionCode 1
        versionName "1.0"

        testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
}

dependencies {

    implementation 'androidx.appcompat:appcompat:1.3.0'
    implementation 'com.google.android.material:material:1.3.0'
    implementation 'androidx.constraintlayout:constraintlayout:2.0.4'

    implementation platform('com.google.firebase:firebase-bom:28.1.0')
    implementation 'com.google.firebase:firebase-analytics'

    testImplementation 'junit:junit:4.13.2'
    androidTestImplementation 'androidx.test.ext:junit:1.1.2'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.3.0'
}



============================================
Lalu klik : Sync Now

Pada Window Firebase maka step 1 akan tertulis : CONNECTED

>> Step 4 : jika berhasil maka ada pesan :


You're all set!

Make sure to check out the documentation to learn how to get started with each Firebase product that you want to use in your app.
You can also explore sample Firebase apps.
Or, continue to the console to explore Firebase.

Klik : Continue to console

(Sekarang akan berada di Console App Firebase)


=================================================================
KEMBALI KE ANDROID STUDIO 
Di Window Firebase > Cloud Messaging.
=================================================================
Pada step 2 : Add FCM to your app

Klik : Add FCM to your app
Disini FCM akan menambahkan : 

<< implementation 'com.google.firebase:firebase-messaging:22.0.0' >>

ke Gradle Module

>> Bila berhasil, maka pada step 2 akan ada centang "Dependencies set up correctly"


=================================================================
KEMBALI KE WEBSITE FIREBASE
Di PROJECTNYA > PROJECT SETTING.
=================================================================

> LALU KE CLOUD Messaging
> COPY SERVER KEY DAN SENDER ID


=================================================================
KEMBALI KE WEBSITE ONE SIGNAL
=================================================================

> Step 1 : Configure App Settings
Masukkan server key dan sender id 
Klik : Save & Continue

> Step 2 : Select SDK
Pilih Native Android
Klik : Save & Continue

> Step 3 : Install and Test
Anda akan peroleh App ID :
Copy App ID tsb

Panduan install : https://documentation.onesignal.com/docs/android-sdk-setup

Ikuti step2nya :
STEP FIREBASE : Installing SDK 

>> Step 1 FB : Requirements
>> Step 2 FB : Add OneSignal Gradle Pliugin and SDK
>> Step 3 FB : Add Required Code 
>> Step 4 FB : Customize the default notification icons ( strongly recommended )



=================================================================
KEMBALI KE ANDROID Studio
=================================================================

Create Application Class - Android Studio

SUGGEST EDITS
1. Open your main AndroidManifest.xml
2. Add android:name=".ApplicationClass" to your <application> tag

XML

<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.test_login_activity">
   <application
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:name=".ApplicationClass">
        ...
    </application>
</manifest>

3. Hover over android:name=".ApplicationClass" or press Alt + Enter or Option + Enter and select Create class 'ApplicationClass'

This will automatically create the class for you. You can do so manually if you choose.

4. Now add the onCreate method to your new Application class.

import android.app.Application;

public class ApplicationClass extends Application {
   @Override
   public void onCreate() {
      super.onCreate();
      // TODO: Add OneSignal initialization here
   }
}


=================================================================
KEMBALI KE FIREBASE INSTALLING SDK :
=================================================================

STEP 3 FIRE BASE : Add Required Code
=====================================

3.1 Add the following to the onCreate method in your Application class.
If you don't have an Application class follow our "Create Application Class Guide".

Cara membuat Application Class : 
https://documentation.onesignal.com/docs/create-application-class-android-studio

(Panduannya di atas)


Setelah itu Coding Application Java Classnya  sbb :
==================================================================

import com.onesignal.OneSignal;

public class MainApplication extends Application {
    private static final String ONESIGNAL_APP_ID = "########-####-####-####-############";
  
    @Override
    public void onCreate() {
        super.onCreate();
        
        // Enable verbose OneSignal logging to debug issues if needed.
        OneSignal.setLogLevel(OneSignal.LOG_LEVEL.VERBOSE, OneSignal.LOG_LEVEL.NONE);
        
        // OneSignal Initialization
        OneSignal.initWithContext(this);
        OneSignal.setAppId(ONESIGNAL_APP_ID);
    }
}

=================================================================
KEMBALI KE ONE SIGNAL UNTUK COPY APP ID :
=================================================================

Copy App IDnya


=================================================================
RUNNING APLIKASI DI EMULATOR
=================================================================

Bila prosesnya berhasil, kembali lagi ke ONE Signal



=================================================================
DI ONE SIGNAL WEBSITE, klik : Check Subscribed Users
=================================================================

Jika proses Running di Emulator berhasil, maka akan tampil perangkat emulator telah menjadi subscriber
Maka prosesnya sdh berhasil.


=================================================================
UJICOBA CLOUD MESSAGING DI ONE SIGNAL
=================================================================


=================================================================
LALU UJICOBA CLOUD MESSAGING DI FIREBASE
=================================================================

Selesai.


=================================================================
STEP TAMBAHAN YANG DIANJURKAN YAITU : BUAT ICON UNTUK NOTIFIKASI
=================================================================

Panduannya di :

https://documentation.onesignal.com/docs/customize-notification-icons

















