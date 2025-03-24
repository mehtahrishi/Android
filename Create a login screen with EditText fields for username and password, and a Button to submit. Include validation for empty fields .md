Here’s how to create a **Login Screen** with **username and password fields** and **validation for empty inputs** in **Android XML and Java**.

---

### **Step 1: Create `activity_login.xml` (UI Design)**
**Go to:**  
📂 `res > layout > Right Click > New > Layout Resource File > Name: activity_login.xml`

**Code for `activity_login.xml`:**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp"
    android:background="@color/backgroundColor">

    <!-- Username Field -->
    <EditText
        android:id="@+id/editTextUsername"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Username"
        android:padding="10dp"
        android:background="@drawable/edit_text_bg"/>

    <!-- Password Field -->
    <EditText
        android:id="@+id/editTextPassword"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Password"
        android:inputType="textPassword"
        android:padding="10dp"
        android:layout_marginTop="10dp"
        android:background="@drawable/edit_text_bg"/>

    <!-- Submit Button -->
    <Button
        android:id="@+id/buttonLogin"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Login"
        android:textSize="18sp"
        android:layout_marginTop="20dp"
        android:background="@drawable/button_bg"/>
</LinearLayout>
```

---

### **Step 2: Create `MainActivity.java` (Login Logic)**
📂 `java > com.example.yourapp > MainActivity.java`

```java
package com.example.yourapp;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private EditText editTextUsername, editTextPassword;
    private Button buttonLogin;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_login);

        // Initialize UI components
        editTextUsername = findViewById(R.id.editTextUsername);
        editTextPassword = findViewById(R.id.editTextPassword);
        buttonLogin = findViewById(R.id.buttonLogin);

        // Set Click Listener on Login Button
        buttonLogin.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                validateInputs();
            }
        });
    }

    // Validation Method
    private void validateInputs() {
        String username = editTextUsername.getText().toString().trim();
        String password = editTextPassword.getText().toString().trim();

        if (username.isEmpty()) {
            editTextUsername.setError("Username is required");
            return;
        }

        if (password.isEmpty()) {
            editTextPassword.setError("Password is required");
            return;
        }

        // If valid, show success message
        Toast.makeText(this, "Login Successful", Toast.LENGTH_SHORT).show();
    }
}
```

---

### **Step 3: Create `edit_text_bg.xml` (For EditText Style)**
📂 `res > drawable > New > Drawable Resource File > Name: edit_text_bg.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">
    <corners android:radius="10dp"/>
    <solid android:color="#FFFFFF"/>
    <stroke android:width="2dp" android:color="#CCCCCC"/>
</shape>
```

---

### **Step 4: Create `button_bg.xml` (For Button Style)**
📂 `res > drawable > New > Drawable Resource File > Name: button_bg.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_pressed="true">
        <shape android:shape="rectangle">
            <corners android:radius="10dp"/>
            <solid android:color="#FF9800"/>
        </shape>
    </item>
    <item>
        <shape android:shape="rectangle">
            <corners android:radius="10dp"/>
            <solid android:color="#FF5722"/>
        </shape>
    </item>
</selector>
```

---

### **Step 5: Set the Theme Colors in `colors.xml`**
📂 `res > values > colors.xml`

```xml
<resources>
    <color name="backgroundColor">#F5F5F5</color>
</resources>
```

---

### **Step 6: Run the Application**
1. **Clean and Rebuild** (`Build > Clean Project` then `Build > Rebuild Project`)
2. **Run the App** (`Shift + F10`)

---

### ✅ **Features Implemented:**
✔ **EditText fields for Username & Password**  
✔ **Button for Login**  
✔ **Input Validation (Empty Check)**  
✔ **Custom UI Styles**  

🚀 **Let me know if you need modifications!**
