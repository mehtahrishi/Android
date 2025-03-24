### **📌 Steps to Implement**
1. **Create an Activity (`MainActivity.java`)** that hosts a Fragment.  
2. **Create a Fragment (`MyFragment.java`)** that receives a string and displays it.  
3. **Use `FragmentTransaction` to replace the Fragment** dynamically.  
4. **Pass data using `setArguments()` and `Bundle`**.  

---

### **1️⃣ Update `activity_main.xml`**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <Button
        android:id="@+id/buttonSend"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send Data to Fragment"/>

    <FrameLayout
        android:id="@+id/fragmentContainer"
        android:layout_width="match_parent"
        android:layout_height="300dp"
        android:layout_marginTop="20dp"/>
</LinearLayout>
```

---

### **2️⃣ Create `MainActivity.java`**
```java
package com.example.fragmentexample;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentManager;
import androidx.fragment.app.FragmentTransaction;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Button buttonSend = findViewById(R.id.buttonSend);

        // Load fragment initially (empty)
        loadFragment(new MyFragment(), null);

        // Set click listener to send data to Fragment
        buttonSend.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String message = "Hello from Activity!";
                MyFragment fragment = new MyFragment();
                Bundle bundle = new Bundle();
                bundle.putString("key_message", message);
                fragment.setArguments(bundle);

                loadFragment(fragment, "MyFragment");
            }
        });
    }

    private void loadFragment(Fragment fragment, String tag) {
        FragmentManager fragmentManager = getSupportFragmentManager();
        FragmentTransaction transaction = fragmentManager.beginTransaction();
        transaction.replace(R.id.fragmentContainer, fragment, tag);
        transaction.commit();
    }
}
```

---

### **3️⃣ Create `MyFragment.java`**
```java
package com.example.fragmentexample;

import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.TextView;
import androidx.annotation.NonNull;
import androidx.annotation.Nullable;
import androidx.fragment.app.Fragment;

public class MyFragment extends Fragment {

    @Nullable
    @Override
    public View onCreateView(@NonNull LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
        View view = inflater.inflate(R.layout.fragment_my, container, false);

        TextView textView = view.findViewById(R.id.textViewMessage);

        // Retrieve passed data
        Bundle bundle = getArguments();
        if (bundle != null) {
            String message = bundle.getString("key_message", "No Message Received");
            textView.setText(message);
        }

        return view;
    }
}
```

---

### **4️⃣ Create `fragment_my.xml`**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="20dp">

    <TextView
        android:id="@+id/textViewMessage"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Waiting for message..."
        android:textSize="18sp"
        android:textStyle="bold"/>
</LinearLayout>
```

---

### **🎯 How It Works**
1. The `MainActivity` initially loads the `MyFragment` without data.
2. When the **button is clicked**, it sends a string `"Hello from Activity!"` to the fragment.
3. The `MyFragment` retrieves the data and displays it in a `TextView`.

---

### ✅ **Run the App and Click the Button!** 🚀  
Your Fragment will **dynamically update** with the received message! 🎉
