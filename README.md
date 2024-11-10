# ReplicatedInteractionMenu_Documentation

# Contents

**2 Components**
- Actor component 
- Character component

**2 Widgets**

- WBP RIM Menu
- WBP RIM Element

**1 Enumerators**
- Interact Actions
	
**1 Structure**
- RIMActions



*+ additional example content used in the showcase map*

---

# Features


- Scrollable interaction menu

- Character component.

- Actor component.

- Enumerator for Interact actions

- Structure containing interact actions and interaction mode

- Component interact delegate

---

# Setup:
 
 Feel free to look at the demonstration character and actors to see how i set it up.

### Character

**#1.** Add BP_RIMInteractionManager to your player character by opening your character blueprint and click add in the components tab and then search for BP_RIMInteractionManager and then click it to add it to your character. This should now appear in your components window and let you change the variables within it.

# 

**#2.** Make sure your character has replication enabled in the details panel and double check that the BP_RIMInteractionManager has "Component Replicates" enabled ( Should be by default ).

#

 **#3.** Adjust the BP_RIMInteractionManager distance in the details panel in BP_RIMInteractionManager that has been added to the character to make sure the trace distance reaches where you want depending on your camera setup (e.g. Firstperson or Thirdperson). You'll be able to see the line trace if you have Debug enabled.
 
#

### Interactable actor

**#1.** Add BP_RIMInteractionComponent the actor by opening the actor blueprint and click add in the components tab and then search for BP_RIMInteractionComponent and then click it to add it the actor. This should now appear in your components window and let you change the variables within it.
#
**#2.** In your newly added BP_RIMInteractionComponent detail panel you'll need to setup the actions you want to use on the actor. To add an action you'll need to find the Actions array located under Replicated Interaction Menu -> Settings - Actions. You can add as many actions as you want by pressing the + sign saying Add Element. See RIMActions Structure for details
#
**#3.** In your newly added BP_RIMInteractionComponent detail panel if you navigate to the Events category, you'll be able to see the On Interact event. If you click the + sign you'll be able to do custom behavior when Interact is called for each actor. Drag out from Actions pin on the newly added On Interact event and type Switch then select "Switch on Enum_InteractActions" then you'll be able to make events for each interaction you'll use. 

#
### Interaction Actions

Just add interactions to Enum_InteractActions found at Enumerators/Enum_InteractActions and you will have more actions you can use.
 


---

# How it works

This works by looking at an actor that has the interaction component. If the actor has one or more interaction actions then it will open the interaction menu.

It will only work if you have added the BP_RIMInteractionManager to your player character. 


---


# Default Inputs
	
- [ Mouse scroll ] - Navigate menu

- [ F ] - Select option


---

# Showcase map

This includes some examples on how you can use the blueprints and recommended mesh requirements in order for it to work properly.

This map uses an example character which is essentially just a First person character template with removed mesh and gun and added Player component.
	

---

# Blueprints


### BP_RIMInteractionManager ( Player component )

This component handles the interaction replication and inputs aswell as showing / creating the menu.

#
**Variables:**

- **Enable Debug (bool)**: 

	This enables debug mode which will alow you to see error messages using print string and draw the line trace used.

- **Trace Distance (float)**:

	This is used to determine how long the line trace will be ( how far you can interact with the blueprints ).

- **Trace Tick Rate (float)**:

	This is how ofen the line trace is getting triggered. lower number means that it ticks faster. ( Used to check if you are looking at an interactable)

- **Enable Input Feedback (bool)**:
	
	The selected menu element will do a quick flicker when you select the option to provide visual feedback when choosing an action.
---

### BP_RIMInteractionComponent ( Actor component )

This component is added to an actor to give it interaction actions and do whatever you need it to do when the delegate is called.


#
**Variables:**

- **Actions (Array < RIMActions Structure >)**:
	This is a array containing all the actions you want on the actor aswell as how it will be called (server only, multicast, client only).



---


### WBP_RIM_Menu ( Widget blueprint )

This is the menu wrapper

To change background color open the blueprint and change it in BackgroundBorder under brush color.

---


### WBP_RIM_Element ( Widget blueprint )

This is an element that is added to the menu wrapper. It contains a label and the interaction Action

**Variables ( Widget Graph ):**

- **DefaultColor (Linear Color)**:
	This is the background color when not hovered. do not  change this one. To change default background for each element, do it in the widget designer. as this get set on initialize by the designer color.
	
- **HoveredColor (Linear Color)**:
	This is the background color when hovered. Change this to your liking.

---


# RIMActions Structure
	
Structure for the Actions.

#
**Variables:**

- **Action (InteractAction Enum)**: 

	Menu action Enumerator

- **bMulticast (bool)**: 
	
	This will multicast the interaction as long as bClientOnly is false

- **bClientOnly (bool)**: 

	The interaction will only happen on the client which interacts with something. Interaction will go through server if this is false.

---

