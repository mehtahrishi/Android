Here’s a step-by-step guide to creating an Android application that displays an **ImageView**, and when clicked, it shows a **Toast message saying "Image Clicked!"**.

---

## **1️⃣ Step 1: Create a New Android Project**
1. Open **Android Studio**.
2. Select **New Project** → **Empty Activity**.
3. Click **Next**, enter the application name (e.g., `ImageClickApp`).
4. Choose **Java** as the language and **Minimum API Level: 21 (Lollipop)**.
5. Click **Finish** and let Android Studio set up your project.

---

## **2️⃣ Step 2: Modify `activity_main.xml`**
- This file defines the **UI layout** with an **ImageView**.
- Place an image in the **res/drawable** folder (`app/res/drawable`).

### **🔹 Code for `activity_main.xml`**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:src="@drawable/sample_image"
        android:contentDescription="Sample Image"
        android:clickable="true"
        android:focusable="true"/>
</LinearLayout>
```
📌 **Note:** 
- Replace `@drawable/sample_image` with your actual image file. Place an image in `res/drawable/` (e.g., `sample_image.png`).

---

## **3️⃣ Step 3: Modify `MainActivity.java`**
- This file adds functionality to **detect clicks** on the ImageView.

### **🔹 Code for `MainActivity.java`**
```java
package com.example.imageclickapp;

import android.os.Bundle;
import android.view.View;
import android.widget.ImageView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Find ImageView by ID
        ImageView imageView = findViewById(R.id.imageView);

        // Set Click Listener on ImageView
        imageView.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Show a Toast message when clicked
                Toast.makeText(MainActivity.this, "Image Clicked!", Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

---

## **4️⃣ Step 4: Update `AndroidManifest.xml` (Optional)**
- If using **custom images**, ensure storage permissions are set **(not required for `res/drawable` images)**.

---

## **5️⃣ Step 5: Run the Application**
1. Click **Run (▶️)** or press **Shift + F10** in Android Studio.
2. The app launches with an **ImageView**.
3. Click the **ImageView**, and a **Toast message ("Image Clicked!")** appears.

✅ **Done!** Your app is working 🎉.
