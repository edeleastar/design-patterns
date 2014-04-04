#NumberPicker

This is our reference documentation:

- <http://developer.android.com/reference/android/widget/NumberPicker.html>

which is a little overwhelming. Back in the guides:

- <http://developer.android.com/guide/components/index.html>

we might find some useful tutorial type introduction to this control - under 'User Interface' - 'Input Controls'

- <http://developer.android.com/guide/topics/ui/controls.html>

.. and this is the page on 'pickers'

- <http://developer.android.com/guide/topics/ui/controls/pickers.html>

This documentation is concerned with Fragments - a concept that may be difficult to grasp initially, and also explores the usage of date and time pickers. 

We can get up and running without this much fuss. Returning to the documentation, these three methods should be sufficient initially:

- <http://developer.android.com/reference/android/widget/NumberPicker.html#setMaxValue(int)>
- <http://developer.android.com/reference/android/widget/NumberPicker.html#setMinValue(int)>
- <http://developer.android.com/reference/android/widget/NumberPicker.html#getValue()>

In onCreate, initialise the values: 

~~~java

    distancePicker.setMinValue(0);
    distancePicker.setMaxValue(20);
~~~

And in createActivityButtonPressed:

~~~java
  public void createActivityButtonPressed (View view) 
  {
    int distance = distancePicker.getValue();
    Log.v("Pacemaker", "CreateActivity Button Pressed with " + distance);
  }
~~~

Run this now - and verify that it operates as expected (see the actual amounts in the log view).

