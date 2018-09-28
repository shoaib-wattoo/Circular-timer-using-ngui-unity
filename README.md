## Objective

Main objective of this blog post is to give you an idea about how to Making a Circular Timer using NGUI.


## Step 1 : Integrate NGUI

**How to Create:**

- First import NGUI in the project. You can download it from here http://forum.unity3d.com/threads/ngui-free-edition.124032/.
- Now, Click on NGUI menu and go to create>2D UI.

![](http://www.theappguruz.com/app/uploads/2015/06/create-2d-ui-1024x576.png)

- Next, take one sprite or texture as shown in the figure below.

##  Step 2 : Scene Setup

![](http://www.theappguruz.com/app/uploads/2015/06/selected-1024x576.png)

- Set that texture or sprite type to ‘filled’ as shown in the figure.
- Set Fill Direction to Radial360.
- Now, take one GameObject and assign CircularTimer script to that object.

![](http://www.theappguruz.com/app/uploads/2015/06/circular-timer-1024x576.png)

- If you want to set circular progress bar to 10 seconds then assign 10 in max time variable (In this example it is 5).
- Now, assign Texture in Timer texture variable if you have taken a texture else create script and take a variable of UISprite instead of UITexture and assign sprite to that variable.

## Step 3 : Code Sample

```csharp
usingUnityEngine;
usingSystem.Collections;
 
publicclassCircularTimer : MonoBehaviour {
 
#region PUBLIC_VARIABLES
publicUITexturetimerTexture;//Timer Texture if There is a sprite and write UISpriteinsted of UITexture.
publicfloatmaxTime;//Max Time For Progress Bar.
#endregion
#region DELEGATES
#endregion
#region UNITY_CALLBACKS
voidOnEnable()
{
StartTurnTimer(maxTime);//Start When Object will Enable.
}
#endregion
#region PUBLIC_METHODS
publicvoidStartTurnTimer(floatmaxTime)//Call This Method When You Want to start Timer.
{
this.maxTime = maxTime;//Set Max Time.
StartCoroutine("StartTimer");
}
publicvoidStopTimer()//Call This Method To Stop Timer.
{
this.gameObject.SetActive(false);
}
#endregion
#region PRIVATE_METHODS
privateIEnumeratorStartTimer()
{
timerTexture.color = Color.green;
float i = 0;
float rate = 1 / maxTime;
while (i < 1)
{
i += rate * Time.deltaTime;
timerTexture.fillAmount = Mathf.Lerp(1, 0, i);
if (i > 0.75f)
timerTexture.color = Color.red;
yieldreturn 0;
}
}
#endregion
}
```

I hope you find this project very helpful while **Circular Timer Using NGUI in Unity**.
