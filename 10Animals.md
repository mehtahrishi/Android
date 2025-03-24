Here's how you can create an **Android application** that displays a list of 10 animals using **ListView** and shows a **Toast message** when an item is clicked.

---
Project name should be Animalapp

### **Step 1: Modify `AndroidManifest.xml`**
Ensure your `AndroidManifest.xml` has the required **main activity**.

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.animalapp">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:supportsRtl="true"
        android:theme="@style/Theme.Animalapp">

        <activity
            android:name=".MainActivity"
            android:exported="true">  <!-- ADDED EXPLICIT EXPORTED ATTRIBUTE -->
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>

</manifest>

```

---

### **Step 2: Design the Layout (`res/layout/activity_main.xml`)**
This file defines the **LinearLayout** and **ListView**.

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <ListView
        android:id="@+id/animalListView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>
    
</LinearLayout>
```

---

### **Step 3: Code the MainActivity (`MainActivity.java`)**
This file sets up the `ListView` and **shows a Toast message** when an item is clicked.

```java
package com.example.animalapp;

import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // List of animals
        String[] animals = {"Lion", "Tiger", "Elephant", "Giraffe", "Zebra", 
                            "Kangaroo", "Panda", "Cheetah", "Wolf", "Dolphin"};

        // Find ListView in the layout
        ListView listView = findViewById(R.id.animalListView);

        // Create an ArrayAdapter (simple list)
        ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, animals);
        listView.setAdapter(adapter);

        // Set item click listener
        listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                String animalName = animals[position]; // Get clicked item
                Toast.makeText(MainActivity.this, "You selected: " + animalName, Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

---

### **Step 4: Run the App**
1. **Launch your app**.
2. **Tap on any animal**, and a Toast message will appear saying:
   ```
   You selected: Lion
   ```
   (or whichever animal you clicked).

---

### **🚀 Features**
✔ **Uses `ListView`** to display 10 animals.  
✔ **Displays `Toast` messages** when an item is clicked.  
✔ **Simple and efficient** implementation using `ArrayAdapter`.

---

✅ **Your Android app is ready!** 🎉
