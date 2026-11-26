# Ex.No: 6 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

1. Start the Android application.
2. Create an XML layout containing an ImageView and six buttons.
3. Add the required image or logo to the drawable folder.
4. Connect the ImageView and buttons with Java code using findViewById().
5. Set click listeners for all six buttons.
6. Implement the following animation operations:
   - Move: Move the image left and right using TranslateAnimation.
   - Blink: Make the image repeatedly visible and invisible using AlphaAnimation.
   - Fade: Gradually fade the image out and back in using AlphaAnimation.
   - Clockwise: Rotate the image by 360 degrees using RotateAnimation.
   - Zoom: Enlarge and reduce the image using ScaleAnimation.
   - Slide: Slide the image from left to its original position using TranslateAnimation.
7. Apply the selected animation to the ImageView using startAnimation().
8. Run the application and test all six animation operations.
9. Stop the application.



## PROGRAM:
```
/*
Program to display animation operation”.
Developed by: Naveen Kumar E
Registeration Number : 212224230181
*/
```

activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fillViewport="true"
    android:background="#F2F2F2">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:gravity="center"
        android:padding="20dp">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Image Animation"
            android:textSize="26sp"
            android:textStyle="bold"
            android:textColor="#222222"
            android:layout_marginBottom="20dp"/>

        <ImageView
            android:id="@+id/imageView"
            android:layout_width="180dp"
            android:layout_height="180dp"
            android:src="@android:drawable/ic_menu_gallery"
            android:scaleType="fitCenter"
            android:contentDescription="Animation Image"
            android:layout_marginBottom="20dp"/>

        <Button
            android:id="@+id/btnMove"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Move"/>

        <Button
            android:id="@+id/btnBlink"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Blink"/>

        <Button
            android:id="@+id/btnFade"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Fade"/>

        <Button
            android:id="@+id/btnRotate"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Clockwise"/>

        <Button
            android:id="@+id/btnZoom"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Zoom"/>

        <Button
            android:id="@+id/btnSlide"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Slide"/>

    </LinearLayout>
</ScrollView>

```
MainActivity.java
```java
package com.example.animations;

import android.os.Bundle;
import android.view.animation.AlphaAnimation;
import android.view.animation.Animation;
import android.view.animation.LinearInterpolator;
import android.view.animation.RotateAnimation;
import android.view.animation.ScaleAnimation;
import android.view.animation.TranslateAnimation;
import android.widget.Button;
import android.widget.ImageView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    ImageView imageView;

    Button btnMove, btnBlink, btnFade;
    Button btnRotate, btnZoom, btnSlide;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);

        btnMove = findViewById(R.id.btnMove);
        btnBlink = findViewById(R.id.btnBlink);
        btnFade = findViewById(R.id.btnFade);
        btnRotate = findViewById(R.id.btnRotate);
        btnZoom = findViewById(R.id.btnZoom);
        btnSlide = findViewById(R.id.btnSlide);

        btnMove.setOnClickListener(v -> moveAnimation());
        btnBlink.setOnClickListener(v -> blinkAnimation());
        btnFade.setOnClickListener(v -> fadeAnimation());
        btnRotate.setOnClickListener(v -> rotateAnimation());
        btnZoom.setOnClickListener(v -> zoomAnimation());
        btnSlide.setOnClickListener(v -> slideAnimation());
    }

    // Move Animation
    private void moveAnimation() {
        resetAnimation();

        TranslateAnimation animation = new TranslateAnimation(
                -100, 100, 0, 0);

        animation.setDuration(1000);
        animation.setRepeatCount(2);
        animation.setRepeatMode(Animation.REVERSE);

        imageView.startAnimation(animation);
    }

    // Blink Animation
    private void blinkAnimation() {
        resetAnimation();

        AlphaAnimation animation = new AlphaAnimation(1.0f, 0.0f);

        animation.setDuration(500);
        animation.setRepeatCount(5);
        animation.setRepeatMode(Animation.REVERSE);

        imageView.startAnimation(animation);
    }

    // Fade Animation
    private void fadeAnimation() {
        resetAnimation();

        AlphaAnimation animation = new AlphaAnimation(1.0f, 0.2f);

        animation.setDuration(1500);
        animation.setRepeatCount(1);
        animation.setRepeatMode(Animation.REVERSE);

        imageView.startAnimation(animation);
    }

    // Clockwise Rotation Animation
    private void rotateAnimation() {
        resetAnimation();

        RotateAnimation animation = new RotateAnimation(
                0, 360,
                Animation.RELATIVE_TO_SELF, 0.5f,
                Animation.RELATIVE_TO_SELF, 0.5f);

        animation.setDuration(1500);
        animation.setInterpolator(new LinearInterpolator());

        imageView.startAnimation(animation);
    }

    // Zoom Animation
    private void zoomAnimation() {
        resetAnimation();

        ScaleAnimation animation = new ScaleAnimation(
                1.0f, 2.0f,
                1.0f, 2.0f,
                Animation.RELATIVE_TO_SELF, 0.5f,
                Animation.RELATIVE_TO_SELF, 0.5f);

        animation.setDuration(1000);
        animation.setRepeatCount(1);
        animation.setRepeatMode(Animation.REVERSE);

        imageView.startAnimation(animation);
    }

    // Slide Animation
    private void slideAnimation() {
        resetAnimation();

        TranslateAnimation animation = new TranslateAnimation(
                -500, 0, 0, 0);

        animation.setDuration(1000);

        imageView.startAnimation(animation);
    }

    // Reset Image Before Every Animation
    private void resetAnimation() {
        imageView.clearAnimation();

        imageView.setAlpha(1.0f);
        imageView.setScaleX(1.0f);
        imageView.setScaleY(1.0f);
        imageView.setRotation(0);
        imageView.setTranslationX(0);
        imageView.setTranslationY(0);
    }
}

```


## OUTPUT

<img width="447" height="977" alt="image" src="https://github.com/user-attachments/assets/a2f24758-0826-4892-9c53-c6e8a5592049" />
<img width="443" height="973" alt="image" src="https://github.com/user-attachments/assets/9a1b4159-1181-4170-97bb-b546e3cc1fd6" />

## RESULT

Thus, the Android application to perform Move, Blink, Fade, Clockwise Rotation, Zoom, and Slide animations on an ImageView using Android Studio was successfully developed and executed.

