<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Falling Animation

<sub>[previous](../second-idle-ii/README.md#user-content-time-out-for-second-idle-ii) • [home](../README.md#user-content-ue4-animations) • [next](../falling-ii/README.md#user-content-falling-animation-ii)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets add an animation for when the player is falling to our movement state machine for when the player falls off the edge of a surface.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Lets go back to [Mixamo](https://www.mixamo.com/#/) and look for some more animations. I am looking for a looping falling animation and for hitting the ground (after falling). Select the character you are using then search for these two animations. First pick the looping falling and make the appropriate adjustments. *Click* the **Download** button.

![go to mixamo and download loop falling animation](images/LoopingFalling.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

*Download* just the animation with the default settings. *Set* **Skin** to `Without Skin` to avoid bringing in any geometry. *Press* the <kbd>Download</kbd> button again.

![download falling animation without skin](images/DownloadJustAnimationFall.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

I also found an animation from falling to hitting the ground. I sped up the animation as I didn't want it to interupt gameplay too much so I cranked up the **Overdrive**. On the next menu it should be the same settings as previously so you can verify this then *press* <kbd>Download</kbd> again.

![download falling hitting ground anim](images/FallingToLanding.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the game and go to the **AJ | Animations** folder and *press* the <kbd>Add/Import</kbd> button and *select* these two animations you just downloaded.

![import animations into unreal](images/ImportFallingAnimation.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

In the **FBX Import Options** overlay, make sure you select the skeleton you have been using. Then press the <kbd>Import All</kbd> button.

![select skeleton then import all](images/SelectSkeletonFallingAnims.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

*Preview* the animations in the editor. *Name* them accordingly. I named them `Falling_Loop` and `Falling_To_Landing`.

![rename animations](images/RenameAndPreviewAnims.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Open the **aj_AnimBlueprint** animation blueprint and go to the **Anim Graph | Core Locomotion** tab. *Right click* on the area and add an **Add State** button.

![press add state button in ainmation blueprint](images/AddFallingState.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Call this new state `Falling`. *Right click* again and select another **Add State** node.

![call state falling and add new state](images/CallItFallingAddAnotherState.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Call* this new state `FallingEnd`.

![call new state FallingEnd](images/FallingEnd.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

Now we need a boolean to track when we are on the ground or in the air. Add a new **Boolean** Variable and call it `bAreWeInAir`. *Make* it **Private** and set the **Tooltip** to `True when player is not on the ground`.

![add are we in air boolean variable](images/AreWeInAirBooleanDef.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: 

Go to the **Event Graph** tab and make some space between the **Is Valid** node and the **Get Velocity** node to check to see if we are in air.

![add space to nodes](images/MakeSpaceEventGraphAnimBP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

*Pull off* of the **Return Value** pin from the **Try Get Pawn Owner** node and *select* the **Get Movement Component** node.

![add get mvoement component node](images/GetMovementComponentAnimBP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Pull off* of the **Return Value** pin from the **Get Movement Component** and select the **IsFalling** node.

![add isfalling node](images/IsFallingVariableGet.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITA`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

*Drag* the **Set Are We In Air** variable onto the graph.

![add set are we in air node](images/SetAreWeInAir.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: 

Connect the **Return Value** pin from the **Is Falling** node to the **Set Are We In Air?** node.

![connect is falling to are we in air nodes](images/ConnectAreWeInAirPins.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITA`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

*Hijack* the execution pin from **Is Valid** node and *send it* to the **Set Are We In Air?** node.

![move execution from is valid to are we in air node](images/IsValidExecutionPin.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Take the output execution pin from **Set Are We in Air?** node to the **Set Speed** node.

![connect are we in air to set speed](images/ReconnectSetSpeedPin.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the new nodes and make a **comment** `Sets Whether Player Is In Air`.

![add code comments](images/AddCommnentIsPlayerInAir.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITA`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the **Anim Graph | Core Locomotion** screen. *Connect* the **IdleWalkRun** state to the **Falling** state to the **Falling End** state *back* to the **IdleWalkRun**.

![connect idlewalkrun to falling to falling end back to idlewalkrun in core locomotion in anim graph](images/ConnectFallingStates.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITA`| :large_blue_diamond: :large_blue_diamond:

Double click the transition from **IdleWalkRun** to **Falling**.

![go to idlewalkrun to falling transition](images/ConditionToFalling.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`ITA`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

*Drag and drop* the **Get Are We In Air?** variable onto the graph.

![add get are we in air node](images/AreWeInAirGetTransition.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Falling Animation II">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../second-idle-ii/README.md#user-content-time-out-for-second-idle-ii)| [home](../README.md#user-content-ue4-animations) | [next](../falling-ii/README.md#user-content-falling-animation-ii)|
|---|---|---|
