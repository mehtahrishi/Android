### **📱 Android Calculator App (Java)**
This guide will help you create a **fully functional calculator** in Android using Java.

---

## **1️⃣ Project Setup**
1. Open **Android Studio**.
2. Create a **New Project** → **Empty Activity**.
3. Set **Language: Java**.

---

## **2️⃣ Design `activity_main.xml` (User Interface)**
We'll create a UI similar to the one in the image, using a **GridLayout** for the buttons.

### **📌 UI Components:**
✔ **EditText** for user input.  
✔ **TextView** for results.  
✔ **Buttons** for digits & operations.

---

### **`activity_main.xml` (Layout File)**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="20dp">

    <!-- Input Display -->
    <EditText
        android:id="@+id/inputField"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter the Value"
        android:gravity="center"
        android:textSize="24sp"
        android:focusable="false"
        android:background="@android:color/transparent"/>

    <!-- Result Display -->
    <TextView
        android:id="@+id/resultView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Result: 0"
        android:textSize="24sp"
        android:textStyle="bold"
        android:gravity="center"
        android:padding="10dp"/>

    <!-- Grid Layout for Buttons -->
    <GridLayout
        android:id="@+id/buttonGrid"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:columnCount="4"
        android:rowCount="5"
        android:padding="10dp">

        <!-- Row 1 -->
        <Button android:id="@+id/btn1" android:text="1"/>
        <Button android:id="@+id/btn2" android:text="2"/>
        <Button android:id="@+id/btn3" android:text="3"/>
        <Button android:id="@+id/btnPlus" android:text="+" android:backgroundTint="#A0A0A0"/>

        <!-- Row 2 -->
        <Button android:id="@+id/btn4" android:text="4"/>
        <Button android:id="@+id/btn5" android:text="5"/>
        <Button android:id="@+id/btn6" android:text="6"/>
        <Button android:id="@+id/btnMinus" android:text="-" android:backgroundTint="#A0A0A0"/>

        <!-- Row 3 -->
        <Button android:id="@+id/btn7" android:text="7"/>
        <Button android:id="@+id/btn8" android:text="8"/>
        <Button android:id="@+id/btn9" android:text="9"/>
        <Button android:id="@+id/btnMultiply" android:text="X" android:backgroundTint="#A0A0A0"/>

        <!-- Row 4 -->
        <Button android:id="@+id/btnDot" android:text="." android:backgroundTint="#A0A0A0"/>
        <Button android:id="@+id/btn0" android:text="0"/>
        <Button android:id="@+id/btnClear" android:text="CE" android:backgroundTint="#A0A0A0"/>
        <Button android:id="@+id/btnDivide" android:text="/" android:backgroundTint="#A0A0A0"/>

    </GridLayout>

    <!-- Submit Button -->
    <Button
        android:id="@+id/btnEqual"
        android:text="Submit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:backgroundTint="#FFD700"
        android:textColor="@android:color/black"
        android:textStyle="bold"
        android:layout_marginTop="10dp"/>

</LinearLayout>
```

---

## **3️⃣ Add Logic in `MainActivity.java`**
This handles button clicks and performs calculations.

### **📌 Logic Implementation**
✔ Append digits to input field.  
✔ Store operator when clicked.  
✔ Perform calculations when "=" is clicked.  
✔ Handle division by zero & clear operation.

---

### **`MainActivity.java`**
```java
package com.example.calculatorapp;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText inputField;
    TextView resultView;
    String input = "";
    double num1, num2;
    char operator;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        inputField = findViewById(R.id.inputField);
        resultView = findViewById(R.id.resultView);

        // Assign Click Listeners
        setNumberClickListener(R.id.btn0, "0");
        setNumberClickListener(R.id.btn1, "1");
        setNumberClickListener(R.id.btn2, "2");
        setNumberClickListener(R.id.btn3, "3");
        setNumberClickListener(R.id.btn4, "4");
        setNumberClickListener(R.id.btn5, "5");
        setNumberClickListener(R.id.btn6, "6");
        setNumberClickListener(R.id.btn7, "7");
        setNumberClickListener(R.id.btn8, "8");
        setNumberClickListener(R.id.btn9, "9");
        setNumberClickListener(R.id.btnDot, ".");

        setOperatorClickListener(R.id.btnPlus, '+');
        setOperatorClickListener(R.id.btnMinus, '-');
        setOperatorClickListener(R.id.btnMultiply, '*');
        setOperatorClickListener(R.id.btnDivide, '/');

        findViewById(R.id.btnEqual).setOnClickListener(v -> calculateResult());
        findViewById(R.id.btnClear).setOnClickListener(v -> clearInput());
    }

    private void setNumberClickListener(int id, String value) {
        findViewById(id).setOnClickListener(v -> {
            input += value;
            inputField.setText(input);
        });
    }

    private void setOperatorClickListener(int id, char op) {
        findViewById(id).setOnClickListener(v -> {
            if (!input.isEmpty()) {
                num1 = Double.parseDouble(input);
                operator = op;
                input = "";
                inputField.setText(""); // Clear for second number input
            }
        });
    }

    private void calculateResult() {
        if (!input.isEmpty()) {
            num2 = Double.parseDouble(input);
            double result = 0;

            switch (operator) {
                case '+': result = num1 + num2; break;
                case '-': result = num1 - num2; break;
                case '*': result = num1 * num2; break;
                case '/': 
                    if (num2 != 0) {
                        result = num1 / num2;
                    } else {
                        resultView.setText("Error: Divide by 0");
                        return;
                    }
                    break;
            }

            resultView.setText("Result: " + result);
            input = "";
        }
    }

    private void clearInput() {
        input = "";
        num1 = num2 = 0;
        operator = '\0';
        inputField.setText("");
        resultView.setText("Result: 0");
    }
}
```

---

## **🎯 Features Implemented**
✅ **User Input Handling** (Digits, Operators)  
✅ **Perform Basic Operations** (+, -, ×, ÷)  
✅ **Handles Divide by Zero Error**  
✅ **Clear Button (CE) Resets Everything**  

### **🛠️ Next Steps**
- Add **Dark Mode** support.  
- Improve UI using **Material Design**.  
- Save history of calculations.

---

### **🚀 Output (App Workflow)**
1️⃣ User enters numbers → **Clicks Operator**  
2️⃣ Enters second number → **Clicks Submit (=)**  
3️⃣ Result displayed.  

Now you have a **fully functional calculator app** in Android Java! 🎉 🚀 Let me know if you need modifications! 😊
