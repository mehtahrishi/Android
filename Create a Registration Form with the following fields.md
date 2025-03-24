Create a Registration Form with the following fields: 
. Username (Text Input) 
Email Address (Text Input) 
Gender (Radio Buttons with options "Male" and "Female") 
Password (Password Input) 
Submit Button  



Here's the Android Studio code for a **Registration Form** using **Java** and **XML**. The form includes:  
- **Username** (Text Input)  
- **Email Address** (Text Input)  
- **Gender** (Radio Buttons: Male & Female)  
- **Password** (Password Input)  
- **Submit Button**  

---

### **Steps to Implement in Android Studio**
1. **Create a new Android project** with an Empty Activity.  
2. **Replace `activity_main.xml`** with the XML code below.  
3. **Replace `MainActivity.java`** with the Java code below.  

---

### **1. XML Layout (`activity_main.xml`)**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <EditText
        android:id="@+id/etUsername"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Username"
        android:inputType="textPersonName" />

    <EditText
        android:id="@+id/etEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Email Address"
        android:inputType="textEmailAddress" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Gender:"
        android:textSize="16sp"
        android:paddingTop="10dp" />

    <RadioGroup
        android:id="@+id/radioGroupGender"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <RadioButton
            android:id="@+id/rbMale"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Male" />

        <RadioButton
            android:id="@+id/rbFemale"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Female" />
    </RadioGroup>

    <EditText
        android:id="@+id/etPassword"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Password"
        android:inputType="textPassword" />

    <Button
        android:id="@+id/btnSubmit"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Register"
        android:layout_marginTop="20dp" />
</LinearLayout>
```

---

### **2. Java Code (`MainActivity.java`)**
```java
package com.example.registrationform;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private EditText etUsername, etEmail, etPassword;
    private RadioGroup radioGroupGender;
    private Button btnSubmit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize UI components
        etUsername = findViewById(R.id.etUsername);
        etEmail = findViewById(R.id.etEmail);
        etPassword = findViewById(R.id.etPassword);
        radioGroupGender = findViewById(R.id.radioGroupGender);
        btnSubmit = findViewById(R.id.btnSubmit);

        // Set click listener for Submit button
        btnSubmit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Get input values
                String username = etUsername.getText().toString().trim();
                String email = etEmail.getText().toString().trim();
                String password = etPassword.getText().toString().trim();

                // Get selected gender
                int selectedGenderId = radioGroupGender.getCheckedRadioButtonId();
                String gender = "";
                if (selectedGenderId != -1) {
                    RadioButton selectedRadioButton = findViewById(selectedGenderId);
                    gender = selectedRadioButton.getText().toString();
                }

                // Validate input
                if (username.isEmpty() || email.isEmpty() || password.isEmpty() || gender.isEmpty()) {
                    Toast.makeText(MainActivity.this, "Please fill all fields", Toast.LENGTH_SHORT).show();
                } else {
                    // Show registration details
                    String message = "Username: " + username + "\nEmail: " + email + "\nGender: " + gender;
                    Toast.makeText(MainActivity.this, message, Toast.LENGTH_LONG).show();
                }
            }
        });
    }
}
```

---

### **3. Run the App**
- This will display a **Registration Form**.  
- Fill in the **Username, Email, Gender, and Password** fields.  
- Click **Register**, and it will display the entered details using a **Toast message**.  

---

### **Additional Features You Can Add**
✔ **Validation** (Check valid email format)  
✔ **Save Data** (Store registration details in SQLite or Firebase)  
✔ **Login Feature** (After registration, allow login)  

Let me know if you need any modifications! 🚀
