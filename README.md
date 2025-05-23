# Hospital-Robot-Simulation
Unity project folder &amp; code for Hopsital Robot Simulation Capstone Project under Prof. Joseph Vybihal (W2025)

## SYSTEM/VERSION REQUIREMENTS

### Unity Version: 2020.3.11f1
Download link to Unity Hub: [https://unity.com/download](https://unity.com/download)

### OS 
* Windows: Windows 7 (SP+), Windows 10 and Windows 11, 64 bit versions only
* macOS: HIgh Sierra 10.13+
* Linux: Ubuntu 20.04, Ubuntu 18.04, and CentOS 7

### CPU
* Windows: x64 architecture with SSE2 instruction set support
* macOS: x64 architecture with SSE2 instruction set support
* Linux: x64 architecture with SSE2 instruction set support

### Graphics API
* Windows: DX10, DX11, and DX12-capable GPUs
* macOS: Metal-capable Intel and AMD GPUs
* Linux: OpenGL 3.2+ or Vulkan-capable, NVIDIA, and AMD GPUs

### Additional requirements:
* Windows: Hardware vendor officially supported drivers
* macOS: Apple officially supported drivers
* Linux: Gnome desktop environment running on top of X11 windowing system, Nvidia official proprietary graphics driver or AMD Mesa graphics driver. Other configuration and user environment as provided stock with the supported distribution (Kernel, Compositor, etc.)

## HOW TO RUN THE SIMULATION

In the Unity editor, move to the Robot_Menu scene in the scenes folder.
While at this scene, click the play button at the top of the editor to start a runtime instance. 

### Controls
* Esc: When in the RobotMenu scene, clicking ESC locates the simulation to the HospitalFloor scene.
* When in a different menu, clicking ESC locates the simulation to the RobotMenu scene.
* When in the HospitalFloor scene, clicking ESC locates the simulation to the RobotMenu scene.
* Assigning tasks to the robot is conducted within the RobotMenu scene, which would locate the simulation to a respective menu depending on the button option selected on the RobotMenu scene.
* The robot would then start conducting the task specified.
* To end the simulation, click on the End Simulation button in the RobotMenu scene.

## BRIEF OVERVIEW OF THE .CS FILES

### DigitalClock.cs
This file configures the clock display to use a 12 hr (AM/PM) or 24 hr display.

### DoorController.cs
This file controls the opening and closing logic of the doors, attached to a “Hinge” Empty GameObject.

### ElevatorDoor.cs
This file is only relevant for the Code Blue protocol. This controls the elevator door opening and provides signals to the nurses to proceed with the protocol.

### EquipmentMenu.cs
This file relates to the EquipmentMenu scene, adding selected equipment to an equipmentList that the robot would be required to deliver.

### FloorCleaningTracker.cs
This file manages the tracking logic of how much and what parts of the room is cleaned during the room cleaning behavior (CleanRoomWithLidar method in RobotManualMovement.cs).

### FoodMenu.cs
This file relates to the FoodMenu scene, adding selected food to a foodList that the robot would be required to deliver.

### NurseMovement.cs, NurseMovement2.cs, NurseMovement3.cs
This file controls the nurse movement during a Code Blue protocol, one for each of the nurse objects, with NurseMovement.cs controlling the actions that occur during Code Blue.

### RobotManualMovement.cs
This file controls the actions that the robot performs. It contains the logic for food delivery, equipment delivery, room cleaning, and relocating the robot back to the charging dock during a Code Blue protocol.

### RobotMenu.cs
This file relates to the RobotMenu scene. It stores the task for the robot to conduct based on the button selected.

### Room.cs
CS file for a Room class.

### RoomCameraController.cs
This file is connected to a RoomCamera GameObject in the HospitalFloor scene, controlling the location of the RoomCamera based on the room selected. The camera gives a top-down view of the room.

### RoomSelection.cs
This file relates to the RoomSelection scene. It stores the room the user selects in the RoomSelection scene, used whenever the robot conducts a task or during Code Blue. Each room on the Hospital Floor image contains a clickable image that is linked to a method in the CS file.

### TaskManager.cs
This file is essentially the database of the simulation. It is attached to a TaskManager Empty GameObject contained in the RobotMenu scene that is not destroyed when switching scenes, thus containing all stored information from other scenes.
* NOTE: As this is contained in the RobotMenu scene and other CS files rely on the variables contained in TaskManager, the simulation would fail if the RobotMenu is not the first scene.

### TimeManager.cs
This file configures how long a day would last within the simulation. Public float dayDuration is configured using seconds; 30f means one day lasts for 30s in real world time. 
