# NASSCOM-VSD-SoC-Design

## Inception of Open-Source EDA, OpenLANE and Sky130nm PDK

1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
2. Calculate the Flop ratio and the percentage of D-FFs.

Running Synthesis
![image](https://github.com/user-attachments/assets/7e74ea30-7885-47af-b10f-233c92e72129)
![image](https://github.com/user-attachments/assets/ddc7eb28-4fa2-4a41-b6af-5e8d59314b0f)

Synthesis Statistics File
![image](https://github.com/user-attachments/assets/c8c0e47b-6ed7-4105-87ef-610cbfd52234)

$$
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops\}{Total\ number\ of\ cells\} = \frac{1613}{14876} = 0.10842
$$


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

$$
Die\ width = 660685
$$

$$
Die\ height = 671405
$$

$$
Die\ width\ in\ microns\ = \frac{660685}{1000} = 660.685\ microns
$$

$$
Die\ height\ in\ microns\ = \frac{671405}{1000} = 671.405\ microns
$$

$$
Area\ of\ die\ in\ microns\ = 660.685 \times 671.405 = 443587.2124\ square\ microns
$$


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


