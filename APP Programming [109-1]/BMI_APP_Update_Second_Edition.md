BMI_Exercise_[11-01]
=================
Activity_main.xml
------------------
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="80dp"
            android:orientation="horizontal">

            <ImageView
                android:id="@+id/imageView"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                app:srcCompat="@drawable/bmi" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="60dp"
            android:orientation="horizontal">

            <TextView
                android:id="@+id/textView"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:text="使用者"
                android:textColor="@color/black"
                android:textSize="24sp" />

            <EditText
                android:id="@+id/inputname"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:ems="10"
                android:hint="名前を入れてください"
                android:inputType="textPersonName" />

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="60dp"
            android:orientation="horizontal">

            <TextView
                android:id="@+id/textView2"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:text="身高"
                android:textColor="@color/black"
                android:textSize="24sp" />

            <EditText
                android:id="@+id/height"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:ems="10"
                android:hint="背を入ってください"
                android:inputType="number"
                android:textSize="18sp" />

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="60dp"
            android:orientation="horizontal">

            <TextView
                android:id="@+id/textView9"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:text="體重"
                android:textColor="@color/black"
                android:textSize="24sp" />

            <EditText
                android:id="@+id/weight"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:ems="10"
                android:hint="体重を入ってください"
                android:inputType="number"
                android:textSize="18sp" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="60dp"
            android:orientation="horizontal">

            <Button
                android:id="@+id/button"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:onClick="BMI"
                android:text="確認"
                android:textSize="24sp"
                app:backgroundTint="@android:color/holo_blue_dark" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="60dp"
            android:orientation="horizontal">

            <Button
                android:id="@+id/button2"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="次のページ"
                android:textSize="24sp"
                app:backgroundTint="@android:color/holo_blue_dark" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="60dp"
            android:orientation="horizontal">

            <TextView
                android:id="@+id/textView3"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:text="使用者："
                android:textColor="@color/black"
                android:textSize="24sp" />

            <TextView
                android:id="@+id/display"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:text="_____________"
                android:textColor="@color/black"
                android:textSize="24sp" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="60dp"
            android:orientation="horizontal">

            <TextView
                android:id="@+id/textView4"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:text="BMI："
                android:textColor="@color/black"
                android:textSize="24sp" />

            <TextView
                android:id="@+id/display2"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:text="_____________"
                android:textColor="@color/black"
                android:textSize="24sp" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="60dp"
            android:orientation="horizontal">

            <TextView
                android:id="@+id/textView5"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:text="診斷："
                android:textColor="@color/black"
                android:textSize="24sp" />

            <TextView
                android:id="@+id/display3"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:text="_____________"
                android:textColor="@color/black"
                android:textSize="24sp" />
        </LinearLayout>
    </LinearLayout>
</androidx.constraintlayout.widget.ConstraintLayout>
```
Activity_main2.xml
------------------
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="90dp"
            android:orientation="horizontal">

            <ImageView
                android:id="@+id/imageView2"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                app:srcCompat="@drawable/bmi" />
        </LinearLayout>

        <TextView
            android:id="@+id/textView13"
            android:layout_width="match_parent"
            android:layout_height="70dp"
            android:gravity="center"
            android:text="結果"
            android:textColor="@color/black"
            android:textSize="30sp" />

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="140dp"
            android:orientation="horizontal">

            <TextView
                android:id="@+id/display4"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:gravity="center"
                android:hint="____________"
                android:textColor="@color/black"
                android:textSize="24sp" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="80dp"
            android:orientation="horizontal">

            <Button
                android:id="@+id/button3"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="ページを戻る"
                android:textSize="24sp"
                app:backgroundTint="@android:color/holo_blue_dark" />
        </LinearLayout>
    </LinearLayout>
</androidx.constraintlayout.widget.ConstraintLayout>
```
MainActivity.java
------------------
```
package com.example.bmi_app_11_01;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import java.text.DecimalFormat;

public class MainActivity extends AppCompatActivity {

    DecimalFormat df = new DecimalFormat("##.00");

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        setTitle("BMI_Page_1_[11-01]");

        Button btn_to_page2 = findViewById(R.id.button2);
        btn_to_page2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent intent = new Intent();
                intent.setClass(MainActivity.this,MainActivity2.class);

                Bundle  bundle = new Bundle();

                bundle.putString("key1",BMI());

                intent.putExtras(bundle);

                startActivity(intent);
            }
        });
    }

    public String BMI() {
        EditText name = findViewById(R.id.inputname);
        EditText height = findViewById(R.id.height);
        EditText weight = findViewById(R.id.weight);

        String name_s = name.getText().toString();
        String height_s = height.getText().toString();
        String weight_s = weight.getText().toString();

        if (!height_s.equals("") && !weight_s.equals("")) {  //(%% ! = NOT)

            Double height_d = Double.parseDouble(height_s);
            Double weight_d = Double.parseDouble(weight_s);
            Double bmi_result = weight_d / ((height_d / 100) * (height_d / 100));

            TextView display = findViewById(R.id.display);
            TextView display2 = findViewById(R.id.display2);
            TextView display3 = findViewById(R.id.display3);

            display.setText(name_s);
            display2.setText(df.format(bmi_result));

            String display_result = display3.getText().toString();
            if (bmi_result < 18.5)
                display3.setText("體重過輕");
            else if (18.5 <= bmi_result && bmi_result < 24)
                display3.setText("正常範圍");
            else if (24 <= bmi_result && bmi_result < 27)
                display3.setText("過重");
            else if (27 <= bmi_result && bmi_result < 30)
                display3.setText("輕度肥胖");
            else if (30 <= bmi_result && bmi_result < 35)
                display3.setText("中度肥胖");
            else if (bmi_result >= 35)
                display3.setText("重度肥胖");

            return name_s + "\n" + " BMI：" + df.format(bmi_result) + "\n" + "診斷：" +  display_result ;
        }
        else{
            return null;
        }
    }

    public void BMI(View view) {
        EditText name = findViewById(R.id.inputname);
        EditText height = findViewById(R.id.height);
        EditText weight = findViewById(R.id.weight);

        String name_s = name.getText().toString();
        String height_s = height.getText().toString();
        String weight_s = weight.getText().toString();

        if (!height_s.equals("") && !weight_s.equals("")) {  //(%% ! = NOT)

            Double height_d = Double.parseDouble(height_s);
            Double weight_d = Double.parseDouble(weight_s);
            Double bmi_result = weight_d / ((height_d / 100) * (height_d / 100));

            TextView display = findViewById(R.id.display);
            TextView display2 = findViewById(R.id.display2);
            TextView display3 = findViewById(R.id.display3);

            display.setText(name_s);
            display2.setText(df.format(bmi_result));

            String display_result = display3.getText().toString();
            if (bmi_result < 18.5)
                display3.setText("體重過輕");
            else if (18.5 <= bmi_result && bmi_result < 24)
                display3.setText("正常範圍");
            else if (24 <= bmi_result && bmi_result < 27)
                display3.setText("過重");
            else if (27 <= bmi_result && bmi_result < 30)
                display3.setText("輕度肥胖");
            else if (30 <= bmi_result && bmi_result < 35)
                display3.setText("中度肥胖");
            else if (bmi_result >= 35)
                display3.setText("重度肥胖");
        }
    }
}
```
MainActivity2.java
------------------
```
package com.example.bmi_app_11_01;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.support.v4.os.IResultReceiver;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        setTitle("BMI_Page_2_[11-01]");

        Bundle bundle = getIntent().getExtras();

        String BMI = bundle.getString("key1","Default");

        TextView display4 = findViewById(R.id.display4);
        display4.setText(BMI);

        Button btn_to_page1 = findViewById(R.id.button3);
        btn_to_page1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent intent = new Intent();
                intent.setClass(MainActivity2.this,MainActivity.class);
                Bundle  bundle = new Bundle();
                startActivity(intent);
            }
        });
    }
}
```
