<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
xmlns:android="http://schemas.android.com/apk/res/android"
 xmlns:app="http://schemas.android.com/apk/res-auto"
 xmlns:tools="http://schemas.android.com/tools"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 tools:context=".MainActivity">
 <TextView
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="41dp"
 android:layout_marginTop="25dp"
 android:layout_marginEnd="80dp"
 android:layout_marginBottom="172dp"
 android:text="SIGN UP ACTIVITY"
 android:textColor="@color/colorAccent"
 android:textSize="28sp"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
 <TextView
 android:id="@+id/textView2"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="22dp"
 android:layout_marginTop="98dp"
 android:layout_marginEnd="346dp"
 android:layout_marginBottom="604dp"
 android:text="Username:"
 android:textSize="18sp"
 android:textStyle="bold"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
 <EditText
 android:id="@+id/editText3"
 android:layout_width="166dp"
 android:layout_height="39dp"
 android:layout_marginStart="124dp"
 android:layout_marginTop="88dp"
 android:layout_marginEnd="54dp"
 android:layout_marginBottom="610dp"
 android:ems="10"
 android:inputType="textPersonName"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
29
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0"/>
 <TextView
 android:id="@+id/textView3"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="22dp"
 android:layout_marginTop="148dp"
 android:layout_marginEnd="346dp"
 android:layout_marginBottom="604dp"
 android:text="Password:"
 android:textSize="18sp"
 android:textStyle="bold"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
 <EditText
 android:id="@+id/editText1"
 android:layout_width="166dp"
 android:layout_height="39dp"
 android:layout_marginStart="124dp"
 android:layout_marginTop="138dp"
 android:layout_marginEnd="54dp"
 android:layout_marginBottom="610dp"
 android:ems="10"
 android:inputType="textPassword"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
 <Button
 android:id="@+id/button"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="108dp"
 android:layout_marginTop="190dp"
 android:layout_marginEnd="215dp"
 android:layout_marginBottom="517dp"
 android:text="SIGN UP"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
</androidx.constraintlayout.widget.ConstraintLayout>





MainActivity.java
30
package com.example.lab3a;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import java.util.regex.Matcher;
import java.util.regex.Pattern;
public class MainActivity extends AppCompatActivity {
 Button signup;
 EditText username, password;
 @Override
 protected void onCreate(Bundle savedInstanceState) {
 super.onCreate(savedInstanceState);
 setContentView(R.layout.activity_main);
 username = findViewById(R.id.editText3);
 password = findViewById(R.id.editText1);
 signup = findViewById(R.id.button);
 signup.setOnClickListener(new View.OnClickListener() {
 @Override
 public void onClick(View view) {
 if(password.getText().toString().length()>=8 && 
validatePassword(password.getText().toString())){
 Toast.makeText(getBaseContext(),"Successful Sign 
UP",Toast.LENGTH_LONG).show();
 Intent it = new Intent(getBaseContext(), login_activity.class);
 Bundle b = new Bundle();
 b.putString("usern",username.getText().toString());
 b.putString("pass",password.getText().toString());
 it.putExtras(b);
 startActivity(it);
 }else{
 Toast.makeText(getBaseContext(),"not 
VALID",Toast.LENGTH_LONG).show();
 }
 }
 });
 }
 public boolean validatePassword(String password){
 Pattern pattern;
 Matcher matcher;
 final String PASSWORD_PATTERN = "^(?=.*[0-9])(?=.*[A-Z])(?=.*[az])(?=.*[@#$%^&+=!])(?=\\S+$).{8,}$";
 pattern = Pattern.compile(PASSWORD_PATTERN);
 matcher = pattern.matcher(password);
 return matcher.matches()
 
 
 
 package com.example.lab3a;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
33
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
public class login_activity extends AppCompatActivity {
 Button lsignin;
 EditText lusername, lpassword;
 int counter = 2;
 @Override
 protected void onCreate(Bundle savedInstanceState) {
 super.onCreate(savedInstanceState);
 setContentView(R.layout.login_activity);
 lusername = findViewById(R.id.l_username);
 lpassword = findViewById(R.id.l_password);
 lsignin = findViewById(R.id.button_signin);
 lsignin.setOnClickListener(new View.OnClickListener() {
 @Override
 public void onClick(View view) {
 Bundle b = getIntent().getExtras();
 String suser = b.getString("usern");
 String spass = b.getString("pass");
 if(suser.toString().equals(lusername.getText().toString()) && 
spass.toString().equals(lpassword.getText().toString()))
 {
 Intent it = new Intent(getBaseContext(), success.class);
 startActivity(it);
 }
 else
 {
 Toast.makeText(getBaseContext(),"LOGIN 
FAILED",Toast.LENGTH_LONG).show();
 }
 counter--;
 if(counter == 0)
 {
 Toast.makeText(getBaseContext(),"FAILED LOGIN 
ATTEMPTS",Toast.LENGTH_LONG).show();
 lsignin.setEnabled(false);
 }
 }
 });
 }
}
success.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
xmlns:android="http://schemas.android.com/apk/res/android"
 xmlns:app="http://schemas.android.com/apk/res-auto"
 xmlns:tools="http://schemas.android.com/tools"
34
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 tools:context=".MainActivity">
 <TextView
 android:id="@+id/textView"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="163dp"
 android:layout_marginTop="300dp"
 android:layout_marginEnd="189dp"
 android:layout_marginBottom="412dp"
 android:text="SUCCESSFULL LOGIN"
 android:textColor="@color/colorAccent"
 android:textSize="30sp"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
success.java
package com.example.lab3a;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
public class success extends AppCompatActivity {
 @Override
 protected void onCreate(Bundle savedInstanceState) {
 super.onCreate(savedInstanceState);
 setContentView(R.layout.success);
 }
}


login_activity.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
xmlns:android="http://schemas.android.com/apk/res/android"
 xmlns:app="http://schemas.android.com/apk/res-auto"
 xmlns:tools="http://schemas.android.com/tools"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 tools:context=".MainActivity">
 <TextView
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="41dp"
 android:layout_marginTop="25dp"
 android:layout_marginEnd="80dp"
 android:layout_marginBottom="172dp"
 android:text="LOGIN ACTIVITY"
 android:textColor="@color/colorAccent"
 android:textSize="28sp"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
 <TextView
 android:id="@+id/textView2"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="22dp"
 android:layout_marginTop="98dp"
 android:layout_marginEnd="346dp"
 android:layout_marginBottom="604dp"
 android:text="Username:"
 android:textSize="18sp"
 android:textStyle="bold"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
 <EditText
 android:id="@+id/l_username"
 android:layout_width="166dp"
 android:layout_height="39dp"
 android:layout_marginStart="124dp"
 android:layout_marginTop="88dp"
 android:layout_marginEnd="54dp"
 android:layout_marginBottom="610dp"
 android:ems="10"
 android:inputType="textPersonName"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
32
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0"/>
 <TextView
 android:id="@+id/textView3"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="22dp"
 android:layout_marginTop="148dp"
 android:layout_marginEnd="346dp"
 android:layout_marginBottom="604dp"
 android:text="Password:"
 android:textSize="18sp"
 android:textStyle="bold"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
 <EditText
 android:id="@+id/l_password"
 android:layout_width="166dp"
 android:layout_height="39dp"
 android:layout_marginStart="124dp"
 android:layout_marginTop="138dp"
 android:layout_marginEnd="54dp"
 android:layout_marginBottom="610dp"
 android:ems="10"
 android:inputType="textPassword"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
 <Button
 android:id="@+id/button_signin"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="108dp"
 android:layout_marginTop="190dp"
 android:layout_marginEnd="215dp"
 android:layout_marginBottom="517dp"
 android:text="SIGN IN"
 app:layout_constraintBottom_toBottomOf="parent"
 app:layout_constraintEnd_toEndOf="parent"
 app:layout_constraintHorizontal_bias="0.0"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent"
 app:layout_constraintVertical_bias="0.0" />
</androidx.constraintlayout.widget.ConstraintLayouT>
