# AboutDialogDemo
ဢၼ်ၼႆႉပဵၼ် activity_about.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="280dp"
    android:layout_height="wrap_content"
    android:layout_gravity="center"
    >

    <FrameLayout
        android:layout_width="fill_parent"
        android:layout_height="fill_parent"
        android:background="@android:color/transparent"
        android:orientation="vertical">

        <android.support.v7.widget.CardView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            app:cardCornerRadius="4dp"
            android:layout_marginTop="32dp"
            android:id="@+id/congratulation_card"
            app:cardBackgroundColor="#FAFAFA"
            app:cardElevation="0dp"
            android:layout_gravity="bottom">
            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:orientation="vertical"
                >
                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center"
                    android:id="@+id/title"
                    android:textSize="18sp"
                    android:textColor="@android:color/primary_text_light"
                    android:layout_marginTop="48dp"
                    android:text="My app"/>
                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center"
                    android:layout_marginTop="24dp"
                    android:layout_marginLeft="32dp"
                    android:textSize="16sp"
                    android:textColor="@android:color/primary_text_light"
                    android:layout_marginRight="32dp"
                    android:id="@+id/message"
                    android:gravity="center"
                    android:text="versionName 1.0"
                    />
                <Button
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="Cost"
                    android:id="@+id/btnOk"
                    android:clickable="true"
                    android:layout_marginTop="32dp"
                    android:textColor="@android:color/white"
                    android:background="@color/colorPrimary"
                    />
            </LinearLayout>
        </android.support.v7.widget.CardView>

        <ImageView
            android:layout_width="64dp"
            android:layout_height="64dp"
            android:padding="1dp"
            android:src="@mipmap/ic_launcher"
            android:layout_gravity="center_horizontal|top"
            />

    </FrameLayout>
</LinearLayout>

ဢၼ်ၼႆႉပဵၼ် ၾႆၢႇ menu
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context="com.android.khurkham.aboutdialog.MainActivity">
    <item
        android:id="@+id/action_settings"
        android:orderInCategory="100"
        android:title="@string/action_settings"
        app:showAsAction="ifRoom"
        android:icon="@drawable/ic_about"/>
</menu>


ၼႂ်း values >> style theme

<resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>

 
    ေတလႆႈၽိူမ်ႉသႃႇတႆၢႇၽႆၢႇတႂ်ႈၼႆႉ ၼႂ်း values >> style theme

    <style name="CustomDialog" parent="@style/Theme.AppCompat.Light.Dialog">
        <item name="windowNoTitle">false</item>
    </style>

</resources>

ေတလႆႈၽိူမ်ႉထႅင်ႈ java
package com.android.khurkham.aboutdialog;


import android.os.Bundle;
import android.os.CountDownTimer;
import android.support.v4.app.DialogFragment;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Button;



/**
 * Main Activity. Inflates main activity xml.
 */
public class AboutDialogFragment extends DialogFragment implements View.OnClickListener {



    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        Button btnOK;
        View view = inflater.inflate(R.layout.activity_about, container, false);
        getDialog().setTitle("About Me");
        btnOK = (Button)view.findViewById(R.id.btnOk);
        btnOK.setOnClickListener(this);
        return view;

    }


   //Dialog
    @Override
    public void onClick(View v) {
        if (v.getId()==R.id.btnOk);
        dismiss();
    }


}

ဢၼ်ၼႆႉတႃႇႁွင်ႉၸႂ်ႉ action icon  ၽိူမ်ႉၼႂ်း MainActivity
 @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            //ပိုတ်ႇAboutActivity
            FragmentManager manager = getSupportFragmentManager();
            AboutDialogFragment aboutInfo = new AboutDialogFragment();
            aboutInfo.setStyle(DialogFragment.STYLE_NO_FRAME,R.style.CustomDialog);
            aboutInfo.show(manager, "About");
            return true;


        }

        return super.onOptionsItemSelected(item);
    }
    
   ၽိူမ်ႉထႅင်ႈဢၼ်ၼႆႉ 
   
       implementation 'com.android.support:design:28.0.0-alpha1'
       implementation 'com.nineoldandroids:library:2.4.0'
    implementation 'com.github.sd6352051.niftydialogeffects:niftydialogeffects:1.0.0@aar'

