#Donate Button

Place a button directly on to the activity - attached to the bottom of the screen as shown:

![Android Visual Designer](../img/x12.png)

Rename both the button and the text field in the Outline view:

![Outline View](../img/x13.png)

Do this by selecting the item and invoking 'Edit ID' from the context menu.

Fix the lint error - and give the button the text 'Donate!'. If all goes as expected, your xml files should be like this:

###activity_donate.xml 

~~~xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context=".CreateActivity" >

    <TextView
        android:id="@+id/createActivityTitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentLeft="true"
        android:layout_alignParentRight="true"
        android:layout_alignParentTop="true"
        android:text="@string/createActivityTitle"
        android:textAppearance="?android:attr/textAppearanceLarge" />

    <Button
        android:id="@+id/createActivityButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:layout_marginBottom="22dp"
        android:text="@string/createActivityButton" />

</RelativeLayout>
~~~

##strings.xml

~~~xml
<?xml version="1.0" encoding="utf-8"?>
<resources>

    <string name="app_name">pacemaker</string>
    <string name="action_settings">Settings</string>
    <string name="createActivityTitle">Enter Activity Details</string>
    <string name="createActivityButton">Create Activity</string>

</resources>
~~~

If there is a deviation from the above - retrace your steps (delete the button) until you can match the above.

We can now switch our attention to the Java Activity class Donate:

~~~java
package org.pacemaker;

import android.os.Bundle;
import android.app.Activity;
import android.view.Menu;

public class CreateActivity extends Activity
{

  @Override
  protected void onCreate(Bundle savedInstanceState)
  {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_create);
  }

  @Override
  public boolean onCreateOptionsMenu(Menu menu)
  {
    // Inflate the menu; this adds items to the action bar if it is present.
    getMenuInflater().inflate(R.menu.create, menu);
    return true;
  }
}
~~~

For any 'controls' a user can interact with we usually find it useful to associate a class member with that object. Currently we have one only on - a Button. The text fields we dont consider 'interactive' as such, so we will not include those.

Insert the following new field into the class:

~~~java
  private Button createActivityButton;
~~~

The class will have to be imported. The class name will always match the name in the Pallette:

![](../img/x14.png)

We are free to call the variable anything we like. However, in order to keep confusion to a minimum, always call the variable by the same name you used in the Outline view:

![](../img/x13.png)

In onCreate - we need to initialise this variable:

~~~java
    createActivityButton = (Button) findViewById(R.id.createActivityButton);
~~~

We might also add a logging message so we can have some feedback as the app launches:

~~~
    Log.v("Pacemaker", "got the CreateActivity button");
~~~

This is the complete activity class:

~~~java
package org.pacemaker;

import android.os.Bundle;
import android.app.Activity;
import android.util.Log;
import android.view.Menu;
import android.widget.Button;

public class CreateActivity extends Activity
{
  private Button createActivityButton;
  
  @Override
  protected void onCreate(Bundle savedInstanceState)
  {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_create);
    
    createActivityButton = (Button) findViewById(R.id.createActivityButton);
    
    Log.v("Pacemaker", "got the CreateActivity button");
  }

  @Override
  public boolean onCreateOptionsMenu(Menu menu)
  {
    // Inflate the menu; this adds items to the action bar if it is present.
    getMenuInflater().inflate(R.menu.create, menu);
    return true;
  }
}
~~~

Finding the log message can be very difficult, unless you set a filter. In the 'LogCat' view in eclipse, create a filter like this:

![](../img/x15.png)

If you then select the filter, we should see our message:

![](../img/x16.png)

