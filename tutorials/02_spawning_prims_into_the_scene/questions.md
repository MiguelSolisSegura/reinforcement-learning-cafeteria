### Questions to Verify Understanding

1. **General Concepts:**
- What is USD (Universal Scene Description) and how is it used in Omniverse?
	- It is a software system and file format developed by Pixar to describe 3D scenes. In Omniverse, is used to design scenes.

- Define the following terms in the context of USD: Primitives (Prims), Attributes, and Relationships.
	- Prims are the basic elements of an USD scene, they can be meshes, lights, cameras. Attributes are the properties of the prims, such as colors, and are described with key-value pairs. The relationships are pointers from one prim to another, for example a mesh that uses a material prim to define its appearance. 
   
- Explain what a USD stage is.
	-  A collection of prims, including their attributes and relationships. This is the same of talking about a *scene*.

2. **Spawning Prims:**
- What is the purpose of the `GroundPlaneCfg` configuration class?
	- It configures a grid with modifiable properties such as appearance and size.
	
- How do you spawn a distant light into the scene? What attributes can you configure for the distant light?
	- From `sim_utils` the `DistantLightCfg` class can be used. According to the documentation, several attributes can be configured such as color, intensity, angle and others.
	
- What is an Xform prim and how is it used when spawning primitive shapes?
	- This type of prim only contains transformation properties. It is useful to transform other prims as a group.

3. **Primitive Shapes:**
- How can you configure the appearance and size of a cone using `ConeCfg`?
	- Setting properties like radius, height and defining a visual material with `PreviewSurfaceCfg`.

- What additional attributes do you need to specify to add rigid body physics to a cone?
	- `rigid_props`, `mass_props` and `collision_props`.

- Describe the difference between visual elements and elements with physics enabled.
	- Visual elements only change the appearance of a prim, physics allow interaction with other prims in the scene. 

4. **Spawning from Files:**
- How do you spawn a USD file into the scene?
	- Using the `UsdFileCfg` and specifying the `usd_path` attribute to point to the desired `.usd` file.
- Explain what it means to add a table as a reference to the scene.
	- It means that any changes made in the reference, will not affect the original file.

5. **Scene Design and Simulation:**
- Why is it important to design the scene before starting the simulation?
	- Adding prims after the simulation has started, can alter the GPU buffer and cause unexpected behaviors.


### Code Assignment

**Assignment: Modify the `spawn_prims.py` Script**

1. **Task Description:**
   Extend the existing `spawn_prims.py` script to include the following functionalities:
   - Print the names of all prims added to the scene.
   - Change the color of one of the spawned cones after a specific number of simulation steps.

2. **Steps:**
   - **Print Names of Prims:**
     - After each prim is spawned, add a print statement to output the name of the prim.
     - **Hint**: the easiest way of doing that there would be to print the names in the `design_scene()` function.

   - **Change Cone Color:**
     - Inside the simulation loop, after a specific number of simulation steps (e.g., 100 steps), change the color of one of the cones by modifying its `visual_material` attribute.
     - **Hint**: Check [omni.isaac.core.utils.prims.set_prim_attribute_value](https://docs.omniverse.nvidia.com/py/isaacsim/source/extensions/omni.isaac.core/docs/index.html#omni.isaac.core.utils.prims.set_prim_attribute_value).

3. **Expected Outcome:**
   - The script should print the names of all prims added to the scene.
   - After the specified number of simulation steps, the color of the selected cone should change, demonstrating dynamic modification of prim attributes during the simulation.