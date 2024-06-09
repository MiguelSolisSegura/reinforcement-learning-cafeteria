### Questions to Verify Understanding

1. **General Concepts:**
- What are the main purposes of the `AppLauncher` and `SimulationContext` classes in Isaac Sim?
    - The `AppLauncher` is required to met the requisite of starting the simulation in Python scrips. The `SimulationContext` gives the user full control over the simulation progress, and also configures the physics scene.

- Why is it necessary to launch the simulation application before importing certain Isaac Sim modules?
	- It is necessary because certain modules of Isaac Sim are only available once the simulation is active and running.

- What command would you use to run the `create_empty.py` script in headless mode?
	- In the following command, the `-p` stands for `python` and the last flag enables headless mode. `./isaaclab.sh -p source/standalone/tutorials/00_sim/create_empty.py --headless`

2. **Launching the Simulator:**
- What is the role of the `argparse.ArgumentParser` in the script?
	- This crates an object used to parse arguments from the CLI.
   
- How does the `AppLauncher.add_app_launcher_args(parser)` method contribute to the script?
	- It configures AppLauncher arguments to work with the argument parser object.
   
- Explain the process and importance of parsing command-line arguments in this context.
	- It allows to use customize the simulation, such as running in headless mode or configuring livestream options.
	
3. **Simulation Context:**
- What does the `SimulationCfg` class configure, and why is it important?
	- It configures fundamental aspects of the simulation, such as the time-step size, gravity, device for computation and the physics engine solver. Is important because allows the user to have greater control over the parameters involved in simulation. 
   
- How is the simulation context initialized, and what parameters are passed during its creation?
	- It is initialized by passing an object of type `SimulationCfg` and the configured physics parameters for that object.

- What is the difference between the `reset()` and `play()` methods of `SimulationContext`?
	- The `reset()` method starts playing the timeline, but it is crucial to initialize the physics handles, so it must be called before stepping the simulator. The `play()` method also plays the timeline, but does not configure the physics handles.

4. **Setting Up the Scene:**
- What is the purpose of the `sim.set_camera_view` method, and what parameters does it take?
	- This method belongs to the `SimulationContext` class and is used to position the viewport camera in the stage. It takes the location of the camera eye, the target for the camera and optionally the primitive path for the camera.
   
5. **Running the Simulation:**
- Explain the logic within the simulation loop that checks if the simulation app is running.
	- The simulation elements progress in time as long as the `simulation_app` objects remains active.
   
- What is the purpose of the `sim.step()` method, and what does the `render` argument control?
	- The method simply steps the physics simulation with the defined time step size. The `render` parameter is a Boolean flag that controls if the scene is rendered after performing the step, or not.

6. **Exiting the Simulation:**
- How is the simulation application closed in the script?
	- It is closed by calling `simulation_app.close()`.
   
- Why is it important to close the simulation application properly?
	- Calling the `close()` method not only allows to stop the simulation, but also close the GUI window.

### Code Assignment

**Assignment: Modify the `create_empty.py` Script**

1. **Task Description:**
   Extend the existing `create_empty.py` script to include a few additional functionalities:
   - Print the current simulation time at each step.

2. **Steps:**
   - **Print Simulation Time:**
     - Inside the simulation loop, add a print statement to output the current simulation time using `sim.get_time()`.

3. **Expected Outcome:**
   - The script should print the current simulation time during each step.
   - The camera view should change after the specified number of steps, demonstrating dynamic camera control within the simulation.