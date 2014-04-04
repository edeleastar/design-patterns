#Activities Model

Create a new package called 'org.pacemaker.models' - and incorporate a new class to represent Activities:

~~~java
package org.pacemaker.models;

import static com.google.common.base.Objects.toStringHelper;
import com.google.common.base.Objects;

public class Activity 
{ 
  public Long   id;
  public String type;
  public String location;
  public double distance;

  public Activity()
  {
  }
  
  public Activity(String type, String location, double distance)
  {
    this.type      = type;
    this.location  = location;
    this.distance  = distance;
  }
  
  @Override
  public String toString()
  {
    return toStringHelper(this).addValue(id)
                               .addValue(type)
                               .addValue(location)
                               .addValue(distance)
                               .toString();
  }
  
  @Override
  public boolean equals(final Object obj)
  {
    if (obj instanceof Activity)
    {
      final Activity other = (Activity) obj;
      return Objects.equal(type, other.type) 
          && Objects.equal(location,  other.location)
          && Objects.equal(distance,  other.distance);    
    }
    else
    {
      return false;
    }
  }
  
  @Override  
  public int hashCode()  
  {  
     return Objects.hashCode(this.id, this.type, this.location, this.distance);  
  }
}
~~~

This use the guava library for utility support:

- <https://code.google.com/p/guava-libraries/>

You will need to download the latest version, copy it into the 'lib' folder of the project, and place it on the path (right clink on the jar file and select 'build path->add to build path')

Back in the CreateActivity, we might create a list to store the activities:

~~~java
  private List<Activity> activities = new ArrayList<Activity>();
~~~

...and populate this list in createActivityButtonPressed:

~~~java
  public void createActivityButtonPressed (View view) 
  {  
    double distance = distancePicker.getValue();
    Activity activity = new Activity (activityType.getText().toString(), activityLocation.getText().toString(), distance);

    activities.add(activity);
    Log.v("Pacemaker", "CreateActivity Button Pressed with " + distance);
  }
~~~

