# Practical_3
AIM: Create Following UI by using Constraint Layout,in one Android application.Create two activities for each layout and use Botton NavigationBar and explicit intent to move from one Activity to another activity.Don’t use Linear Layout in Constraint Layout and vice-versa.

CODE:
LoginActivity.kt:

package ru.kotlin.a20012011183_yatharthpatel

import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.text.method.LinkMovementMethod
import android.widget.TextView
import ru.kotlin.a20012011183_yatharthpatel.databinding.ActivityLoginBindin g
import
ru.kotlin.a20012011183_yatharthpatel.databinding.ActivityMainBinding

class LoginActivity : AppCompatActivity() {
private lateinit var binding: ActivityLoginBinding

override fun onCreate(savedInstanceState: Bundle?) {
super.onCreate(savedInstanceState)
binding = ActivityLoginBinding.inflate(layoutInflater) setContentView(binding.root)

setSupportActionBar(binding.toolbar)

val signup = findViewById<TextView>(R.id.signup) signup.setOnClickListener {
Intent(this, RegisterActivity::class.java).also
{startActivity(it)}

signup.movementMethod = LinkMovementMethod.getInstance();

}

binding.bottomNavigationView.selectedItemId =
R.id.bottom_nav_login
binding.bottomNavigationView.setOnItemSelectedListener { it
 

 
->
when (it.itemId) { R.id.bottom_nav_reg -> {
Intent(this, RegisterActivity::class.java).also
{ startActivity(it) }
}
}
return@setOnItemSelectedListener true
}
}
}


RegistrationActivity.kt:

package ru.kotlin.a20012011183_yatharthpatel

import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.text.method.LinkMovementMethod
import android.widget.TextView
import ru.kotlin.a20012011183_yatharthpatel.databinding.ActivityMainBinding import ru.kotlin.a20012011183_yatharthpatel.databinding.ActivityRegisterBin ding

class RegisterActivity : AppCompatActivity() {
private lateinit var binding: ActivityRegisterBinding
override fun onCreate(savedInstanceState: Bundle?) {
super.onCreate(savedInstanceState)
binding = ActivityRegisterBinding.inflate(layoutInflater) setContentView(binding.root)

setSupportActionBar(binding.toolbar)
val login = findViewById<TextView>(R.id.logins) login.setOnClickListener {
 

 
Intent(this, LoginActivity::class.java).also
{startActivity(it)}

login.movementMethod = LinkMovementMethod.getInstance();

}
binding.bottomNavigationView.selectedItemId =
R.id.bottom_nav_reg
binding.bottomNavigationView.setOnItemSelectedListener { it
->
when (it.itemId) { R.id.bottom_nav_login -> {
Intent(this, LoginActivity::class.java).also {
startActivity(it) }
}
}
return@setOnItemSelectedListener true
}
}
}


MainActivity.kt:

package ru.kotlin.a20012011183_yatharthpatel

import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

import ru.kotlin.a20012011183_yatharthpatel.ActivityMainBinding

class MainActivity : AppCompatActivity() {
private lateinit var binding: ActivityMainBinding
override fun onCreate(savedInstanceState: Bundle?) {
super.onCreate(savedInstanceState)
binding = ActivityMainBinding.inflate(layoutInflater) setContentView(binding.root)

setSupportActionBar(binding.toolbar)
Intent(this, LoginActivity::class.java).also {startActivity(it)}
}
}
 

 


activity_login.xml:

<?xml version="1.0" encoding="utf-8"?>
<androidx.coordinatorlayout.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android" xmlns:app="http://schemas.android.com/apk/res-auto" xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent" android:layout_height="match_parent" tools:context=".LoginActivity">

<com.google.android.material.appbar.AppBarLayout android:id="@+id/appBarLayout" android:layout_width="match_parent" android:layout_height="wrap_content" android:fitsSystemWindows="true">


<com.google.android.material.appbar.MaterialToolbar android:id="@+id/toolbar" android:layout_width="match_parent" android:layout_height="match_parent" app:layout_scrollFlags="scroll|enterAlways|snap"
/>

<ImageView
android:layout_width="match_parent" android:layout_height="180sp" android:src="@drawable/guni_pink_logo" android:contentDescription="Logo"
/>

<androidx.constraintlayout.widget.ConstraintLayout android:id="@+id/bigbossparent" android:layout_width="match_parent" android:layout_height="match_parent" tools:context=".LoginActivity">
 

 
<com.google.android.material.card.MaterialCardView android:id="@+id/mainbox" android:layout_width="match_parent" android:layout_height="290sp" android:layout_marginHorizontal="23sp" android:layout_marginVertical="15sp" app:cardBackgroundColor="#E6D3FB" app:cardCornerRadius="20sp" app:cardElevation="7sp" app:layout_constraintBottom_toBottomOf="parent" app:strokeColor="@color/black" tools:ignore="MissingConstraints"
>


<com.google.android.material.textfield.TextInputLayout
android:id="@+id/email"

style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox" android:layout_width="280sp" android:layout_height="80sp" android:layout_gravity="center_horizontal" android:layout_marginVertical="30sp" app:boxStrokeColor="@color/black" app:layout_constraintEnd_toEndOf="parent" app:layout_constraintStart_toStartOf="parent" app:layout_constraintTop_toBottomOf="parent"
>

<com.google.android.material.textfield.TextInputEditText
android:layout_width="match_parent" android:layout_height="66dp"

android:drawableEnd="@drawable/ic_baseline_email_24"
android:drawableTint="#DA3D90" android:hint="Email" android:inputType="textEmailAddress" android:textColorHint="#9C27B0" />
 

 

</com.google.android.material.textfield.TextInputLayout>


<com.google.android.material.textfield.TextInputLayout
android:id="@+id/password"

style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox" android:layout_width="280sp" android:layout_height="80dp" android:layout_gravity="center_horizontal" android:layout_marginVertical="120sp" app:boxStrokeColor="@color/black" app:layout_constraintEnd_toEndOf="parent" app:layout_constraintStart_toStartOf="parent" app:layout_constraintTop_toBottomOf="@id/email"
>

<com.google.android.material.textfield.TextInputEditText
android:layout_width="match_parent" android:layout_height="65dp"

android:drawableEnd="@drawable/ic_baseline_vpn_key_24"
android:drawableTint="#DA3D90" android:hint="Password" android:inputType="textEmailAddress"
/>

</com.google.android.material.textfield.TextInputLayout>


</com.google.android.material.card.MaterialCardView>


<TextView
android:id="@+id/forgotpass" android:layout_width="wrap_content" android:layout_height="wrap_content"
 

 
android:text="Forgot Password?" app:layout_constraintBottom_toBottomOf="parent" app:layout_constraintStart_toStartOf="parent" android:layout_marginVertical="70sp" android:layout_marginHorizontal="183sp" android:textColor="@color/black" android:autoLink="all"
android:textSize="18sp" android:elevation="7sp" tools:ignore="MissingConstraints"
>
</TextView>

<androidx.constraintlayout.widget.ConstraintLayout android:layout_width="wrap_content" android:layout_height="60sp" android:elevation="7sp" android:layout_marginHorizontal="128sp" app:layout_constraintBottom_toBottomOf="parent" app:layout_constraintStart_toStartOf="parent" android:layout_marginBottom="-15sp"
>

<Button
android:id="@+id/bt" android:layout_width="150sp" android:layout_height="50sp" android:backgroundTint="#6200ee" android:text="Login" android:textSize="18sp" app:cornerRadius="40sp" tools:ignore="MissingConstraints,NotSibling"
/>

</androidx.constraintlayout.widget.ConstraintLayout>

</androidx.constraintlayout.widget.ConstraintLayout>

</com.google.android.material.appbar.AppBarLayout>
 

 

<androidx.core.widget.NestedScrollView android:id="@+id/nestedScrollView" android:layout_width="match_parent" android:layout_height="match_parent" android:layout_marginBottom="50dp" app:layout_behavior="@string/appbar_scrolling_view_behavior" tools:ignore="SpeakableTextPresentCheck">

<androidx.constraintlayout.widget.ConstraintLayout android:layout_width="wrap_content" android:layout_height="wrap_content"

app:layout_behavior="@string/appbar_scrolling_view_behavior" android:layout_marginTop="70sp"
>

<TextView
android:id="@+id/t1" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Don't have a account?" android:textSize="17sp" tools:ignore="MissingConstraints" app:layout_constraintLeft_toLeftOf="parent" android:layout_marginLeft="70sp"
>
</TextView>

<TextView
android:id="@+id/signup" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Sign Up" android:textSize="17sp" android:textColor="#DA3D90" android:textStyle="bold" android:textAllCaps="true" tools:ignore="MissingConstraints" app:layout_constraintLeft_toLeftOf="@+id/t1"
 

 
android:layout_marginLeft="190sp"
>
</TextView>

</androidx.constraintlayout.widget.ConstraintLayout>
</androidx.core.widget.NestedScrollView>


<com.google.android.material.bottomnavigation.BottomNavigationView android:id="@+id/bottomNavigationView" android:layout_width="match_parent" android:layout_height="wrap_content" android:layout_gravity="bottom" app:layout_anchor="@+id/nestedScrollView" app:layout_anchorGravity="bottom|center"

app:layout_behavior="com.google.android.material.behavior.HideBottom ViewOnScrollBehavior"
app:menu="@menu/navigation_menu" />


</androidx.coordinatorlayout.widget.CoordinatorLayout>


activity_registration.xml:

<?xml version="1.0" encoding="utf-8"?>
<androidx.coordinatorlayout.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android" xmlns:app="http://schemas.android.com/apk/res-auto" xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent" android:layout_height="match_parent" tools:context=".RegisterActivity">

<com.google.android.material.appbar.AppBarLayout android:layout_width="match_parent" android:layout_height="wrap_content" android:fitsSystemWindows="true" android:background="@color/white"
 

 
>

<com.google.android.material.appbar.MaterialToolbar android:id="@+id/toolbar" android:layout_width="match_parent" app:layout_scrollFlags="scroll|enterAlways|snap" android:layout_height="?attr/actionBarSize" />


</com.google.android.material.appbar.AppBarLayout>

<androidx.core.widget.NestedScrollView android:layout_width="match_parent" android:layout_height="match_parent"

app:layout_behavior="com.google.android.material.appbar.AppBarLayout
$ScrollingViewBehavior"
>
<LinearLayout
android:layout_width="match_parent" android:layout_height="match_parent" android:orientation="vertical" android:layout_marginTop="-40sp"
>

<ImageView
android:layout_width="match_parent" android:layout_height="180sp" android:layout_marginBottom="-45sp" android:src="@drawable/guni_pink_logo"
/>
<com.google.android.material.card.MaterialCardView android:layout_width="match_parent" android:layout_height="523sp" android:layout_marginHorizontal="23sp" android:layout_marginVertical="15sp" android:backgroundTint="#E6D3FB" app:cardCornerRadius="20sp" app:cardElevation="7sp" app:strokeColor="@color/black"
 

 
tools:ignore="MissingConstraints"
>


<com.google.android.material.textfield.TextInputLayout
android:id="@+id/username"

style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox" android:layout_width="280sp" android:layout_height="80sp" android:layout_gravity="center_horizontal" android:layout_marginVertical="30sp" app:boxStrokeColor="@color/black">


<com.google.android.material.textfield.TextInputEditText
android:layout_width="match_parent" android:layout_height="66dp"

android:drawableEnd="@drawable/ic_baseline_person_24"
android:drawableTint="#DA3D90" android:hint="User Full Name" android:inputType="text" android:textColorHint="#9C27B0" />


</com.google.android.material.textfield.TextInputLayout>


<com.google.android.material.textfield.TextInputLayout
android:id="@+id/phone"

style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox" android:layout_width="280sp" android:layout_height="80sp" android:layout_gravity="center_horizontal" android:layout_marginVertical="105sp" app:boxStrokeColor="@color/black">
 

 
<com.google.android.material.textfield.TextInputEditText
android:layout_width="match_parent" android:layout_height="66dp"

android:drawableEnd="@drawable/ic_baseline_phone_android_24"
android:drawableTint="#DA3D90" android:hint="Phone Number" android:inputType="number" android:textColorHint="#9C27B0" />


</com.google.android.material.textfield.TextInputLayout>


<com.google.android.material.textfield.TextInputLayout
android:id="@+id/city"

style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox" android:layout_width="280sp" android:layout_height="80sp" android:layout_gravity="center_horizontal" android:layout_marginVertical="180sp" app:boxStrokeColor="@color/black">


<com.google.android.material.textfield.TextInputEditText
android:layout_width="match_parent" android:layout_height="66dp"

android:drawableEnd="@drawable/ic_baseline_person_24"
android:drawableTint="#DA3D90" android:hint="City" android:inputType="text" android:textColorHint="#9C27B0" />


</com.google.android.material.textfield.TextInputLayout>


<com.google.android.material.textfield.TextInputLayout
 

 
android:id="@+id/email"

style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox" android:layout_width="280sp" android:layout_height="80sp" android:layout_gravity="center_horizontal" android:layout_marginVertical="255sp" app:boxStrokeColor="@color/black">


<com.google.android.material.textfield.TextInputEditText
android:layout_width="match_parent" android:layout_height="66dp"

android:drawableEnd="@drawable/ic_baseline_email_24"
android:drawableTint="#DA3D90" android:hint="Email" android:inputType="textEmailAddress" android:textColorHint="#9C27B0" />


</com.google.android.material.textfield.TextInputLayout>


<com.google.android.material.textfield.TextInputLayout
android:id="@+id/pass"

style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox" android:layout_width="280sp" android:layout_height="80sp" android:layout_gravity="center_horizontal" android:layout_marginVertical="330sp" app:boxStrokeColor="@color/black">


<com.google.android.material.textfield.TextInputEditText
android:layout_width="match_parent" android:layout_height="66dp"

android:drawableEnd="@drawable/ic_baseline_vpn_key_24"
 

 
android:drawableTint="#DA3D90" android:hint="Password" android:inputType="textPassword" android:textColorHint="#9C27B0" />


</com.google.android.material.textfield.TextInputLayout>


<com.google.android.material.textfield.TextInputLayout
android:id="@+id/confirmpasss"

style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox" android:layout_width="280sp" android:layout_height="80sp" android:layout_gravity="center_horizontal" android:layout_marginVertical="405sp" app:boxStrokeColor="@color/black">


<com.google.android.material.textfield.TextInputEditText
android:layout_width="match_parent" android:layout_height="66dp"

android:drawableEnd="@drawable/ic_baseline_vpn_key_24"
android:drawableTint="#DA3D90" android:hint="Confirm Password" android:inputType="textEmailAddress" android:textColorHint="#9C27B0" />


</com.google.android.material.textfield.TextInputLayout>

</com.google.android.material.card.MaterialCardView>

<LinearLayout
android:layout_width="wrap_content" android:layout_height="match_parent" android:layout_gravity="center_horizontal" android:elevation="10sp"
 

 
android:orientation="vertical" android:layout_marginTop="-45sp" android:layout_marginBottom="80sp"
>
<Button
android:id="@+id/b" android:layout_width="135sp" android:layout_height="50sp" android:backgroundTint="#6200ee" android:text="Register" android:textSize="19sp" android:elevation="10sp" app:cornerRadius="40sp" android:layout_gravity="center_horizontal"
tools:ignore="MissingConstraints,NotSibling" />

<TextView
android:id="@+id/tss" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Do you have an account?" android:textSize="17sp" tools:ignore="MissingConstraints" android:layout_marginTop="30sp"
>
</TextView>

<TextView
android:id="@+id/logins" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Login" android:textSize="17sp" android:textColor="#DA3D90" android:textStyle="bold" android:textAllCaps="true" tools:ignore="MissingConstraints" android:layout_marginLeft="200sp" android:layout_marginTop="-23sp"
>
 

 
</TextView>

</LinearLayout>
</LinearLayout>
</androidx.core.widget.NestedScrollView>


<com.google.android.material.bottomnavigation.BottomNavigationView android:id="@+id/bottomNavigationView" android:layout_width="match_parent" android:layout_height="wrap_content" android:layout_gravity="bottom"

app:layout_behavior="com.google.android.material.behavior.HideBottom ViewOnScrollBehavior"
app:menu="@menu/navigation_menu" />
</androidx.coordinatorlayout.widget.CoordinatorLayout>


activity_main.xml:

<?xml version="1.0" encoding="utf-8"?>
<androidx.coordinatorlayout.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto" xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent" android:layout_height="match_parent" tools:context=".MainActivity">

<TextView
android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Hello World!" app:layout_constraintBottom_toBottomOf="parent" app:layout_constraintEnd_toEndOf="parent" app:layout_constraintStart_toStartOf="parent" app:layout_constraintTop_toTopOf="parent" />
 

 
<com.google.android.material.appbar.AppBarLayout android:layout_width="match_parent" android:layout_height="wrap_content" android:fitsSystemWindows="true">

<com.google.android.material.appbar.MaterialToolbar android:id="@+id/toolbar" android:layout_width="match_parent" app:layout_scrollFlags="scroll|enterAlways|snap" android:layout_height="?attr/actionBarSize" />

</com.google.android.material.appbar.AppBarLayout>
<androidx.core.widget.NestedScrollView android:layout_width="match_parent" android:layout_height="match_parent" android:layout_marginBottom="50dp"

app:layout_behavior="@string/appbar_scrolling_view_behavior">
<androidx.constraintlayout.widget.ConstraintLayout android:layout_width="match_parent" android:layout_height="wrap_content"

app:layout_behavior="@string/appbar_scrolling_view_behavior">
</androidx.constraintlayout.widget.ConstraintLayout>
</androidx.core.widget.NestedScrollView>

</androidx.coordinatorlayout.widget.CoordinatorLayout>

OUTPUT:

!image](https://user-images.githubusercontent.com/93566991/190939655-6d53612e-e541-4491-8739-2a9c7166af2a.png)

![image](https://user-images.githubusercontent.com/93566991/190939736-61ea551d-ca7c-4c13-88fc-8117e7af6cd5.png)

![image](https://user-images.githubusercontent.com/93566991/190939764-84faa737-176d-474a-ba63-3ecca90fdd6e.png)

![image](https://user-images.githubusercontent.com/93566991/190939778-d2bfccb5-47af-4610-8d8b-def020d3acc2.png)

