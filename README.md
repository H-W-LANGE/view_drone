# ViewDrone Plugin
## User Manual

After installing the plugin its button should be located in the toolbar as shown on the image below:
![image](https://github.com/H-W-LANGE/view_drone/assets/135021163/117bbdb4-1f1c-4ffc-b26e-c6fd77f9a89e)
When pressing the button the User Interface will pop up, prompting the user to add their
input layers and values as following:

![image](https://github.com/H-W-LANGE/view_drone/assets/135021163/9f2f38a4-5077-4b5e-834f-7cd0eeeba715)

For clarity the values have been sketched on the figure below, as well as listed in a table,
providing some examples:

![inputs](https://github.com/H-W-LANGE/view_drone/assets/135021163/64f7e631-7f8d-49c8-a7bc-7de027d58aa2)

It is very important that the units are consistent in all of the inputs, the user should strive to use the height unit used in the DSM, otherwise, the output of the plugin will be unreliable. The different layers should also use the same Coordinate Reference System (CRS), and in case the CRS of the input layers are mismatched they should be reprojected properly before using them in the plugin.

![image](https://github.com/H-W-LANGE/view_drone/assets/135021163/c396d4d3-d1ba-418a-82d4-ef680b3738ef)

The observer and target height are both fixed values that will depend on the specific drone and drone pilot, but the range and grid size are a bit harder to determine and should be selected based on the specific area of interest polygon. The computation time is mostly affected by the number of grid points since the plugin will compute a viewshed for each point in the grid, so a smaller grid size will obviously result in a longer computation time. Therefore it is very important to take this into account when deciding on the grid size. The user should strive towards a compromise between having an adequate number of grid points, without making the point grid so dense that the calculations are too time-consuming. The size of the area polygon also has a huge impact, since the grid size is defined by the distance between the points, and will scale that to the area of the polygon. It is recommended to use a larger grid size for larger areas in order to keep the computation time as short as possible. The range should be large enough to cover an adequate amount of the area polygon, without extending unnecessarily far outside its borders. The type and size of the drone should also be taken into consideration.

### Other notes for the user

Please note that if the same folder is used for multiple computations with the plugin, the old result will be overwritten in the output directory, so remember to either rename or move the output files before using the plugin again. It will, however, not overwrite the layers in QGIS, so it is still possible to export the old layers if they are still present in the QGIS project.

While the plugin is a helpful tool for planning drone flights, it is important to note the limitations of the plugin, and of course use common sense, when planning a drone flight. A big disadvantage of using the DSM for the viewshed calculations is that you risk that some of the points will be located on top of a structure, such as a building or a tree, and the algorithm will therefore calculate the viewshed from that point, which could result in that location being registered as an area where the conditions are satisfied. But in reality that location will most likely not be an option, one of the only exceptions being a flat roof that the pilot has access to. So it is very important to double-check with satellite images, orthophoto, or similar during the planning phase.


It is also important to note when the DSM was created, and potentially investigate if there have been any major changes in the area since the DSM was created. The DSM can obviously not take the structures that weren't present at the time of the data capture into account. So any buildings that were constructed after the DSM was created should be considered, especially if the DSM is older.

