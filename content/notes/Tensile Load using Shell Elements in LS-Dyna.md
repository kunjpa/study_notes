Tensile Load on Shell Element

## Step 1: Create Mesh Part

## Step 2: Define Material model

- Go to page 3. Click *Mat  to define material properties.

- To see full list of material models, select “ALL”. From the list select appropriate model for analysis. For this problem we are doing elastic analysis, so choose “001-ELASTIC” from the list. Click edit.

- A dialogue box will open. Click NewID. Give appropriate title to material. In RO, enter Density of material in appropriate unit system, Enter Young Modulus in E filed, and poison ration under PR field. Click accept. Click done. Save K file. 

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg)

Fig 1: Material Properties of Aluminum

- After defining material model, define section. Go to Page 3. Click *Section button. As we are performing analysis on shell, click on “SHELL”, click edit. A dialogue box will open. 1

- Click NEWID. Give appropriate title to shell section.

- In T1 add thickness of shell element in appropriate units.

- In ELEFORM, you’ll have various option for element formation of shell. By default it will be on “2”.

- You can Keep it to default, or choose, integrated shell element formation. For that select “16” in ELEFORM list. Integrated shell elements will help to resolve hourglassing defect, but it will take slightly more time to complete the simulation as it introduce virtual or invisible nodes in the model.

- If you have more than one shell and you want to compare different shell element formation, you can define, different shell element formation and assign them to different mesh in next step.

- To define another shell element formation, click newID. Choose the element formation type in ELEFORM list. Click accept. Click done. Save K file.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image004.jpg)

Fig 2: (a) Default shell settings

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image006.jpg)

Fig 2: (b) Shell integrated settings

- After defining section, now assign the material model and section to appropriate mesh part.

- Go to Page 3. Click *Part, from the list select part click edit. A dialogue box will open.

- Click NewID. Give appropriate title to part. If you have multiple part, then instead of clicking NewID enter the Part ID manually in PID.

- In SECID, choose the section you want to assign to the part. In MID, select the material model define earlier.

- Click accept. If you only have one part, click done. Save K file.

- If you have more part, after clicking accept, enter Part ID of next part in PID. Give appropriate title, and assign SECID and MID for new part. Click accept, and repeat the process for all the parts. Click Done. Save K file.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image008.jpg)

Fig 3: (a) Part 1 definition

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image010.jpg)

Fig 3: (b) Part 2 definition

## Step 3: Define Boundary condition

- In this problem of tensile load, one edge will be fixed, other edge will be constrained to move only in one direction.

- Tensile load will be applied to other edge. Load should be applied on each node such that, total load is equal to applied load.

- To Fix the edge, go to page 5. Click spc. Click create. In the bottom left, select By elements in Sel.Nodes column, check the Prop option. Now select the edge you want to fix for all part.

- If the whole edge is not selected, when prop option is checked, it is possible that model have duplicate nodes. Remove duplicate nodes and then start the process again.

- Select all the edges that you want to fix, and from the option, check the boxes of X,Y,Z, RX,RY, and RZ to constrain linear and rotational movement of selected edges. Click apply. Click done. Save K file.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image012.jpg)

Fig 4: (a) select edge option

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image014.jpg)

Fig  4 : (b) edge constrain setting

- Now select nodes on which load will be applied.

- Go to page 5. Click *SetID, to create node set for different parts. Click Create. Select *SET_NODE option. Give appropriate title to nodeset. Select the loading edge of the part one at a time. Create different nodeset for each part’s loading edge.

- To select the entire edge, select by element in Sel.Node column and check Prop box, similar to above step. Click apply.

- Give appropriate tiltle to next nodeset. Select the loading edge of next part, and select the edge. Click apply. Repeat this for all loading edges. Click done. Save k file.

- In nodenum, you can see number of nodes on each edge in the node set list. This will come in handy while applying load on each node.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image016.jpg)

Fig 5: Node set

- Before applying load, we need to define loading curve. Loading curve will help to apply the load gradually on the part, as we don’t want to analyze impact loading condition in this problem.

- To define load time curve, go to page 3. Click *Define. From the list select “CURVE” option. Click edit. A dialogue box will open. Click NewID, give appropriate title to the curve.

- Enter value of X co-ordinate in A1 filed and Y Co-ordinate in O1 field. Click insert. Enter another point, click insert. After inserting all required points, click accept, and then click plot to check if points entered are correct or not. If you click plot before clicking accept, you won’t see any plot and all the entered point will be erased. Click done. Save K file.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image018.jpg)

Fig 6: Load time curve

- Now Go to page 3. Click *Load. From the list select NODESET, click edit. A dialogue box will open.

- From NSID, choose the Note Set ID from the list. This will be the node sets you created in page 5 SetID. In DOF select the direction of the applied load, in this case load is applied on the positive Y direction. Now in LCID select the load-time curve from the list.

- For SF, scale factor, use this equation to calculate load on each node.

- Load on each node = (Total load applied on whole edge)/(number of node on the edge).

- You can get number of node on a particular edge, from page 5 SetID, Node set list. See figure 5 for example.

- Click accept. Select another nodeset to apply load on loading edge of next part. Repeat these steps for all loading edges. Click done. Save K file.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image020.jpg)

Fig 7: Load on Nodes

## Step 4: Add Keycards to control simulation

- In this step we will add simulation duration and solver settings.
- For this simulation we will be using Implicit solver.
- If you want to use explicit solver, define time-step curve in page 3 *Define option. as step 8 in discrete element modelling notes. And then add time-step card in page 3 *Control. And only add Implicit solver key card. Keep IMFLAG to default value “0” and add DT2SIM value.
- For solving problem implicitly, follow below steps.
-  Go to page 3. Click *Control. From the list select Termination, click edit. A dialogue box will open. In ENDTIM, enter the time duration you want to run simulation for, in appropriate units. Keep everything else to default. Click accept. Click done. Save K file.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image022.jpg)

Fig 8: Termination time

- Now to add Implicit Auto Card. Go to page 3. Click *Control. From the list select IMPLICIT AUTO, click edit. A dialogue box will open.
- Keep everything to default. Click accept. Click done. Save K file.
- Keeping everything to default will ensure that solver will take constant timestep.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image024.jpg)

Fig 9: Keep Implicit Auto to default settings.

- Now Implicit Dynamics. Go to page 3. Click *Control. From the list select IMPLICIT DYNAMICS, click edit. A dialogue box will open. Keep everything to default. Click accept. Click done. Save K file.
- We need to do static simulation in this problem, and by default, implicit dynamics is set for static simulation.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image026.jpg)

Fig 10: Keep Implicit Dynamics to default settings.

- Now add Implicit General keycard. Go to page 3. Click *Control. From the list select IMPLICIT GENRAL, click edit. A dialogue box will open. Change IMFLAG to “1” from default setting of “0”. IMFLAG “1” option is for Implicit solver.
- DT0 is the initial time step. Taking Initial Time step as = (simulation duration)/(number of data points required).
- Keep everything to default. Click accept. Click done. Save K file.

![](file:///C:/Users/kunj/AppData/Local/Temp/msohtmlclip1/01/clip_image028.jpg)

Fig 10:Implicit General settings

## Step 5: Add Keycards to get simulation output

-  In this simulation we mainly need, GLSAT, and MATSAT in ASCII option, and Binary D3 Plot.
-  History node is optional.
-  You can follow step 9 in the Discrete element model notes for this step.