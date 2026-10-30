# Ex.No:2a Develop program to create a text field and a button “Navigate”. When you enter “www.gmail.com” and press navigate button it should open google page using Implicit Intents.


## AIM:

To create a navigate button using Implicit Intent to display the gmail page using Android Studio.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
1.Launch the Android application.
2.Create an Implicit Intent object.
3.Specify the required action (ACTION_VIEW, ACTION_DIAL, ACTION_SEND, etc.).
4.Attach the required data using Uri.parse().
5.Invoke startActivity() with the Intent.
6.Android searches for a compatible application.
7.Display the app chooser if multiple apps are available.
8.Launch the selected application.
9.Perform the requested action.


## PROGRAM:
```
/*
Program to print the text “Implicit intent”.
Developed by: Rithesh S
Registeration Number : 212225220084
*/
```
## MainActivity.java
```
package com.example.implicit;

import android.content.ActivityNotFoundException;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button button = findViewById(R.id.btn);
        EditText editText = findViewById(R.id.editText);

        button.setOnClickListener(v -> {
            String rawUrl = editText.getText().toString().trim();

            if (rawUrl.isEmpty()) {
                Toast.makeText(this, "Please enter a URL", Toast.LENGTH_SHORT).show();
                return;
            }

            String url = (rawUrl.startsWith("http://") || rawUrl.startsWith("https://"))
                    ? rawUrl
                    : "https://" + rawUrl;

            try {
                Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));
                startActivity(intent);
            } catch (ActivityNotFoundException e) {
                Toast.makeText(this, "No application found to handle this URL", Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```
## Activity.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#E02DE2C3"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="sans-serif-black"
        android:lineSpacingExtra="86sp"
        android:text="@string/title_implicit"
        android:textAppearance="@style/TextAppearance.AppCompat.Body2"
        android:textColor="#D3FF4501"
        android:textSize="24sp"
        app:layout_constraintBottom_toTopOf="@+id/editText"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_chainStyle="packed" />

    <EditText
        android:id="@+id/editText"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="72dp"
        android:layout_marginTop="100dp"
        android:layout_marginEnd="72dp"
        android:hint="@string/hint_enter_url"
        android:importantForAutofill="no"
        android:inputType="textUri"
        app:layout_constraintBottom_toTopOf="@+id/btn"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="88dp"
        android:shadowColor="#000000"
        android:text="@string/btn_search"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editText"
        app:strokeColor="#0A0909" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

## OUTPUT
<img width="1920" height="1080" alt="Screenshot 2026-10-30 110759" src="https://github.com/user-attachments/assets/57ce87ba-84a4-41e5-bea7-8d6608b1fe83" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/47feee32-35d0-4d6e-8f59-9eb9dbe5a6f6" />


## RESULT
Thus a Simple Android Application create a navigate button using Implicit Intent to display the gmail page using Android Studio is developed and executed successfully.


