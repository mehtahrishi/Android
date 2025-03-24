### **Android Resources and Their Uses in an Application**  

In Android, **resources** are used to define values and assets separately from the code. This allows easy modifications and better organization of styles, colors, strings, and images.

We will create a simple **Android app** that uses:
- **Colors** (`colors.xml`)
- **Themes** (`themes.xml`)
- **Strings** (`strings.xml`)
- **Drawables** (Vector icons or shapes)
- **Dimensions** (`dimens.xml`)
- **Images** (From the `res/drawable` folder)

---

## **🚀 Step 1: Create a New Android Studio Project**
1. **Open Android Studio**  
2. **Click** `New Project`  
3. **Select** `Empty Activity` and click **Next**  
4. **Enter details:**
   - **Name**: `ResourceDemo`
   - **Package Name**: `com.example.resourcedemo`
   - **Language**: `Java`
   - **Minimum SDK**: `API 21 (Android 5.0 Lollipop)`
5. **Click Finish** and wait for the project to set up.

---

## **🚀 Step 2: Define Android Resources**
### 1️⃣ **Define Colors (`res/values/colors.xml`)**
**Path:** `res/values/colors.xml`
```xml
<resources>
    <color name="primaryColor">#6200EE</color>
    <color name="secondaryColor">#03DAC5</color>
    <color name="backgroundColor">#FFFFFF</color>
    <color name="textColor">#000000</color>
</resources>
```
✅ **Usage:** We use these colors for buttons, text, and backgrounds.

---

### 2️⃣ **Define Theme (`res/values/themes.xml`)**
**Path:** `res/values/themes.xml`
```xml
<resources xmlns:tools="http://schemas.android.com/tools">
    <style name="Theme.ResourceDemo" parent="Theme.MaterialComponents.Light">
        <item name="colorPrimary">@color/primaryColor</item>
        <item name="colorSecondary">@color/secondaryColor</item>
        <item name="android:windowBackground">@color/backgroundColor</item>
    </style>
</resources>
```
✅ **Usage:** This theme is applied to the entire app.

---

### 3️⃣ **Define Strings (`res/values/strings.xml`)**
**Path:** `res/values/strings.xml`
```xml
<resources>
    <string name="app_name">Resource Demo</string>
    <string name="welcome_text">Welcome to the Resource Demo App!</string>
    <string name="button_text">Click Me</string>
</resources>
```
✅ **Usage:** Used for **TextView** and **Button** labels.

---

### 4️⃣ **Define Dimensions (`res/values/dimens.xml`)**
**Path:** `res/values/dimens.xml`
```xml
<resources>
    <dimen name="text_size">18sp</dimen>
    <dimen name="padding">16dp</dimen>
</resources>
```
✅ **Usage:** Defines **text size and padding** for UI elements.

---

### 5️⃣ **Add Drawables (Shapes) (`res/drawable/rounded_button.xml`)**
**Path:** `res/drawable/rounded_button.xml`
```xml
<shape xmlns:android="http://schemas.android.com/apk/res/android" android:shape="rectangle">
    <corners android:radius="12dp"/>
    <solid android:color="@color/secondaryColor"/>
</shape>
```
✅ **Usage:** This is used as a **background for buttons**.

---

### 6️⃣ **Add an Image (`res/drawable/logo.png`)**
1. **Download an image (e.g., logo.png)**  
2. **Copy and Paste it** into the `res/drawable/` folder.

✅ **Usage:** This image is displayed in an `ImageView`.

---

## **🚀 Step 3: Update `activity_main.xml` (UI Layout)**
1. **Go to** `res/layout/activity_main.xml`
2. **Replace the content with this:**
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="@dimen/padding"
    android:background="@color/backgroundColor">
    <!-- ADDED ID -->
    <ImageView
        android:id="@+id/logoImageView"
    android:layout_width="150dp"
    android:layout_height="150dp"
    android:src="@drawable/logo"
    android:contentDescription="@string/app_name"
    android:layout_marginBottom="20dp"/>

    <!-- ADDED ID -->
    <TextView
        android:id="@+id/welcomeTextView"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/welcome_text"
    android:textColor="@color/textColor"
    android:textSize="@dimen/text_size"
    android:layout_marginBottom="20dp"/>

    <Button
        android:id="@+id/myButton"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/button_text"
    android:textSize="@dimen/text_size"
    android:textColor="@color/backgroundColor"
    android:background="@drawable/rounded_button"/>
    </LinearLayout>

   ```
✅ **This UI displays:**
- A **logo image**
- A **welcome text**
- A **styled button** with a rounded background.

---

## **🚀 Step 4: Update `MainActivity.java`**
1. **Go to** `app/src/main/java/com/example/resourcedemo/`
2. **Open `MainActivity.java`**
3. **Replace everything with this:**
   ```java
   package com.example.resourcedemo;

   import android.os.Bundle;
   import android.widget.Button;
   import android.widget.ImageView;
   import android.widget.TextView;
   import android.widget.Toast;
   import androidx.appcompat.app.AppCompatActivity;

   public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Linking UI components with correct IDs
        ImageView logoImageView = findViewById(R.id.logoImageView);
        TextView welcomeTextView = findViewById(R.id.welcomeTextView);
        Button myButton = findViewById(R.id.myButton);

        // Button click event
        myButton.setOnClickListener(v ->
                Toast.makeText(MainActivity.this, "Button Clicked!", Toast.LENGTH_SHORT).show()
        );
    }
}

   ```
✅ **This adds a `Toast` message when the button is clicked.**

---

## **🚀 Step 5: Run the App**
1. **Click** the Play button ▶️  
2. The app will launch on your **Emulator or Phone**  
3. You should see:
   - A **logo image**
   - A **welcome message**
   - A **clickable button with a rounded background**
4. **Click the button** ➝ A **Toast message** appears (`Button Clicked!`).

---

## **🎯 Expected Output**
| Feature | Demonstrated Resource |
|---------|---------------------|
| **Colors** | Used in `background`, `button`, `text` |
| **Themes** | Applied to the whole app |
| **Strings** | Used for UI labels |
| **Drawables** | Used for button styling |
| **Dimensions** | Used for `text size` and `padding` |
| **Images** | Displayed in `ImageView` |

✅ **Congratulations! You have successfully demonstrated the use of Android Resources!** 🎉  

Let me know if you need any modifications! 🚀🔥
