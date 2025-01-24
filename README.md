# NASSCOM-VSD-SoC-Design

## Inception of Open-Source EDA, OpenLANE and Sky130nm PDK

1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
2. Calculate the Flop ratio and the percentage of D-FFs.

Running Synthesis
![image](https://github.com/user-attachments/assets/7e74ea30-7885-47af-b10f-233c92e72129)
![image](https://github.com/user-attachments/assets/ddc7eb28-4fa2-4a41-b6af-5e8d59314b0f)

Synthesis Statistics File
![image](https://github.com/user-attachments/assets/c8c0e47b-6ed7-4105-87ef-610cbfd52234)

Flop Ratio = (Number of D Flip Flops) / (Total number of cells) = 1613 / 14876 = 0.10842


## Good Floorplan vs bad floorplan and introduction to library cells
1. Run the 'picorv32a' design floorplan using OpenLANE Flow
2. Calculate the die area in microns from the floorplan def
3. Load the generated floorplan in magic tool
4. Run the 'picorv32a' design congestion aware placement in the OpenLANE flow
5. Load the generated placement in the magic tool

Running Floorplan
![image](https://github.com/user-attachments/assets/2f41a03c-3713-4a62-83c0-850dbf438072)
![image](https://github.com/user-attachments/assets/73823ad5-564f-4bbf-8689-6b01dcb21432)

Floorplan Layout using Klayout<br>
![image](https://github.com/user-attachments/assets/5e8f0a2e-f36d-46b2-9ba6-b288684a4acb)

According to floorplan,  1000 unit distance = 1 micron

Die width = 660685

Die height = 671405

Die width in microns = 660685 / 1000 = 660.685 microns

Die height in microns = 671405 / 1000 = 671.405 microns

Area of die in microns = 660.685 * 671.405 = 443587.2124 square microns


Floorplan Analysis using Magic Tool
![image](https://github.com/user-attachments/assets/9fd052b2-da64-4d75-9661-33074708c108)
Horizontal and Vertical port cells
![image](https://github.com/user-attachments/assets/48399356-0780-4a36-938f-1d1c944239ab)
![image](https://github.com/user-attachments/assets/5ad62537-1d2f-461d-8dac-714d32ce713f)
Decoupling capacitors and Tap cells
![image](https://github.com/user-attachments/assets/92c4313f-7607-4b32-bdce-03af1542e862)
<br>
Running placement
![image](https://github.com/user-attachments/assets/faa397a2-40b3-4ff9-afe7-72cc92e20401)
![image](https://github.com/user-attachments/assets/1d602b2e-3689-4831-b172-549bbcc80ba9)
Placement Analysis using Magic Tool
![image](https://github.com/user-attachments/assets/50b1543e-b95d-4ccc-a5b5-92119b0944b5)
Powerlines
![image](https://github.com/user-attachments/assets/5ca24744-5ee4-40d1-8fe7-d0afea6a9a37)


## Design library cell using Magic Layout and ngspice characterization

1. Using the IO placer to change the distance between tap cells
2. Clone the standard cell design for an inverter from a github repository
3. Load the invertor layout in magic tool
4. Performing spice extraction of invertor in magic tool
5. Editing the SPICE model file and graphical simulation
6. Find the error in the magic tech file and fix them

Changing the spacing between the port cells
![image](https://github.com/user-attachments/assets/7633970e-4f23-4f9a-9df8-79e79b6265c3)
![image](https://github.com/user-attachments/assets/ced14750-1709-4166-aeaf-5244cfd3c2b6)

Cloning the std cell design for inverter
![image](https://github.com/user-attachments/assets/fce23dc4-11c6-4ddb-a99b-b27a02ca8da9)

Loading the inverter layout using Magic Tool
![image](https://github.com/user-attachments/assets/511c55ab-be71-4f8f-8ac9-05d710386790)
Identifying PMOS and NMOS
![image](https://github.com/user-attachments/assets/52c02f14-922b-4587-b639-35ef3dbc6958)
![image](https://github.com/user-attachments/assets/de04f66f-e1dc-4ad4-87b3-36503517a4e1)
Output Y connectivity to PMOS and NMOS drain verified
![image](https://github.com/user-attachments/assets/333e1771-b7a7-4c44-b792-17f27a423f72)
PMOS source connectivity to PWR verified
![image](https://github.com/user-attachments/assets/293b6a93-f8bf-401f-ac0d-426edb64387a)
NMOS source connectivity to GND verified
![image](https://github.com/user-attachments/assets/3b7dd681-2af6-45b9-938e-e0fe7e0f8e36)

Creating a Spice File through tkcon
![image](https://github.com/user-attachments/assets/e2504306-f4db-4c7d-9d13-e3a8d09f6075)
![image](https://github.com/user-attachments/assets/1ccfd030-0759-46c2-974b-2ec33d7014c0)

Measuring unit distance in layout grid
![image](https://github.com/user-attachments/assets/d93ade76-f671-4622-9771-3af3c51a3783)

Edited Spice File
![image](https://github.com/user-attachments/assets/8932b44b-c669-434c-9aff-b49faff7f31a)
Plotting the graph using ngspice
![image](https://github.com/user-attachments/assets/2a544903-65a4-4957-9083-a9e25040a4db)
![image](https://github.com/user-attachments/assets/7596034d-b23e-4dde-98a3-bd5f9f19c228)

1. Rise Time
   The time taken for the output waveform to transition from 20% to 80% of its maximum value.

   Rise transition time = 2.2673 - 2.1942 = 0.0731 ns

2. Fall Time
   The time taken for the output waveform to transition from 80% to 20% of its maximum value.

   Fall transition time = 4.0754 - 4.0378 = 0.0376 ns

3. Cell Rise Delay
   The time taken for a 50% transition at the output (0 to 1) corresponding to a 50% transition at the input (1 to 0).

   Cell rise delay = 2.2102 - 2.1675 = 0.0427 ns

4. Cell fall delay
   The time taken for a 50% transition at the output (1 to 0) corresponding to a 50% transition at the input (0 to 1).

   Cell fall delay = 4.0842 - 4.0621 = 0.0221 ns

Downloading the corrupted file 
![image](https://github.com/user-attachments/assets/068f45d4-b85b-437f-8b98-a2012604e23b)
![image](https://github.com/user-attachments/assets/92854843-0b22-4050-abbe-72e54772e8a1)
.magicrc file 
![image](https://github.com/user-attachments/assets/dd30fb92-64aa-437e-9273-a040ed65fe8e)
![image](https://github.com/user-attachments/assets/ff843762-438a-4242-a76c-41c581ffb5b8)
Fixing errors
![image](https://github.com/user-attachments/assets/ff51fdfc-5330-4569-8dda-db965362c6f3)
![image](https://github.com/user-attachments/assets/7c9a2bc1-6534-4c84-b5fe-1c2a897f605c)


## Pre-layout timing analysis and importance of good clock tree

1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.
2. Save the finalized layout with custom name and open it.
3. Generate lef from the layout.
4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.
6. Run openlane flow synthesis with newly inserted custom inverter cell.
7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.
9. Do Post-Synthesis timing analysis with OpenSTA tool.
10. Make timing ECO fixes to remove all violations.
11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.
12. Post-CTS OpenROAD timing analysis.
13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.


Setting up the grid
![image](https://github.com/user-attachments/assets/9dccb099-06d2-4c75-9ca2-263396af8fa7)
The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
![image](https://github.com/user-attachments/assets/6ceb6cd0-7fdb-4e84-a959-2c555b15f16f)

Generating a lef file from the layout
![image](https://github.com/user-attachments/assets/969e647b-9034-4f49-96d2-c83f569da8b3)
![image](https://github.com/user-attachments/assets/58a386d4-c03e-4f30-9167-614f9a5bffad)

Copying the lef file to another directory
![image](https://github.com/user-attachments/assets/597c9b45-8fdc-4446-817a-6df8abea3517)

Edited config file
![image](https://github.com/user-attachments/assets/286301de-b180-495a-ba84-38d54435c92c)

Running synthesis using the custom inverter cell
![image](https://github.com/user-attachments/assets/bf4577e8-ec27-4fda-a4f3-b30c369350a3)
![image](https://github.com/user-attachments/assets/d6775adc-55cb-45cc-b229-71c824d0ad3d)

Modifying design parameters to improve timing
![image](https://github.com/user-attachments/assets/86bdd0cf-830b-4cda-9f16-d8d99a450186)
![image](https://github.com/user-attachments/assets/c86081b9-c5ed-4589-8ddb-e53da29d48bd)

Running Floorplan
![image](https://github.com/user-attachments/assets/7877c37d-28fb-4b22-977c-8ce7411fa1d0)
![image](https://github.com/user-attachments/assets/2ce2c497-db29-44a5-bd36-cdebdfeaac95)
![image](https://github.com/user-attachments/assets/e56abcbf-616f-4df8-840b-64ff30ff9aa4)

Timing Analysis
![image](https://github.com/user-attachments/assets/921d4e94-6fa4-4526-a470-430b62f6f812)
Newly created pre_sta.conf for STA analysis in openlane directory
![image](https://github.com/user-attachments/assets/9598f5ae-11cd-43ea-8890-ef822960017c)
Newly created my_base.sdc for STA analysis in openlane/designs/picorv32a/src directory
![image](https://github.com/user-attachments/assets/9d9b5fe8-6aba-40f0-96cf-a88edd3e66fa)

![image](https://github.com/user-attachments/assets/cc41819d-1a7b-4641-b735-7f88a9c98b58)

Replacing the old netlist with a new one 
![image](https://github.com/user-attachments/assets/e8c04c36-5b9d-4261-bde3-8fe1cdaf309d)


## Final steps for RTL2GDS using tritonRoute and openSTA

1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.
2. Perfrom detailed routing using TritonRoute.
3. Post-Route parasitic extraction using SPEF extractor.
4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.
