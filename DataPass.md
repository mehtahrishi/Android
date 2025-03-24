### **Android App: Passing Data Between Activities Using Intent**
This app will **pass user input (name) from one activity to another** using an Intent.

---

### **Step 1: Create a New Android Project**
1. **Open Android Studio**.
2. **Create a New Project** → Select **Empty Activity**.
3. **Name** the app (e.g., `PassDataApp`), choose **Java**, and click **Finish**.

---

### **Step 2: Modify `AndroidManifest.xml`**
📂 **`AndroidManifest.xml`** (Register the second activity)
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.PassDataApp"
        tools:targetApi="31">

        <!-- Main Activity -->
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <!-- Second Activity (Missing in your file) -->
        <activity
            android:name=".SecondActivity"
            android:exported="true" />

    </application>

</manifest>

```

---

### **Step 3: Modify `activity_main.xml`**  
📂 **`res > layout > activity_main.xml`**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <EditText
        android:id="@+id/editTextName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter your name" />

    <Button
        android:id="@+id/buttonSend"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send Data"
        android:layout_marginTop="20dp"/>
</LinearLayout>
```

---

### **Step 4: Modify `MainActivity.java`**
📂 **`java > com.example.passdata > MainActivity.java`**
```java
package com.example.passdata;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private EditText editTextName;
    private Button buttonSend;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editTextName = findViewById(R.id.editTextName);
        buttonSend = findViewById(R.id.buttonSend);

        buttonSend.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String name = editTextName.getText().toString();

                // Create Intent to send data to SecondActivity
                Intent intent = new Intent(MainActivity.this, SecondActivity.class);
                intent.putExtra("USER_NAME", name);
                startActivity(intent);
            }
        });
    }
}
```

---

### **Step 5: Create `SecondActivity.java`**
📂 **`java > com.example.passdata > SecondActivity.java`**
```java
package com.example.passdata;

import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    private TextView textViewResult;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        textViewResult = findViewById(R.id.textViewResult);

        // Get data from intent
        Intent intent = getIntent();
        String name = intent.getStringExtra("USER_NAME");

        // Display the received data
        textViewResult.setText("Hello, " + name);
    }
}
```

---

### **Step 6: Create `activity_second.xml`**
📂 **`res > layout > activity_second.xml`**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <TextView
        android:id="@+id/textViewResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Received Data"
        android:textSize="20sp"
        android:textStyle="bold"/>
</LinearLayout>
```

---

### **Step 7: Run the App**
1. **Enter a name** in the `EditText` field.
2. **Press the "Send Data" button**.
3. **The Second Activity will open** and display `"Hello, [Entered Name]"`.

---

### ✅ **Features Implemented**
✔ **Uses Intent** to pass data between activities.  
✔ **Displays user input** in another activity.  
✔ **Simple and clear** Android app structure.

🚀 **Run and test it!** 🎯
