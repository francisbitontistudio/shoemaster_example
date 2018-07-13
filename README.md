# Conformal Lattice Example

The Conformal Lattice example requires few API calls to be accomplished.

### 1. Export Surface Grid

[DIAGRAM HERE OF HOW TO PREPARE THE SURFACE]


The prepared json file can be uploaded through http post request to the endpoint:
https://studiobitonti.appspot.com/storage/upload

Or using provided uploader example:
* <a href='g3doc/installation.md'>Upload</a><br>

### 2. Create Conformal Grid

Use the API endpoint: https://studiobitonti.appspot.com/conformalGrid to construct a list of box-shaped scaffold.

Example input:
```python
{
  "u":40, # how many time to divide the surfaces in each direction 
  "v":8,
  "w":4, 
  "surfaces": "sole_example.json",  # input file name saved on server representing the surfaces
  "filename": "grid_example.json",  # output file name to be saved on server
  "directOutput": true, # if true the content of output file will be returned by the API call, otherwise, the location of the file will be returned instead.
  "unitize": false # whether to reparametricise the surface division
}
```

Example output:
```python
[
  [
    [0,0.5,0.7],[0,1.2,2.3],[3.5,-0.2,0.7],[2.5,3.2,2.22],[5.25,6.12,1.12],[5.1,-12.2,3.3],[4.6,0.11,-8] # 3d coordinates for 8 corners of a box
  ],
  [
    [4.1,0.5,0.2],[6,1.42,1.3],[4.2,3.2,5.1],[2.3,3.1,5.52],[7.28,6.72,5.42],[5.4,11.2,5.3],[22.6,2.44,1.2]
  ],
  # [[...],[...]....[...]]...... list of boxes composing the conformal grid
]
```

* <a href='g3doc/installation.md'>live demo</a><br>
<p align="center">
  <img src="imgs/grid.JPG" width=8000>
</p>

### 3. Create Lattice Unit 

Use the API endpoint: https://studiobitonti.appspot.com/conformalGrid to generate a parametrically described lattice unit

Example input:
```python
{
  "case": 5, # choose the category of unit as integer range from 0 to 7
  "chamfer": 0.3, # the chamfer percentage from 8 corners as float from 0 to 0.5
  "centerChamfer": 0.0,  # the chamfer percentage from center as float from 0 to 0.5
  "bendIn": 0.0, # the bend in percentage for each outside edges as float from 0 to 0.5
  "cBendIn": 0.0, # the bend in percentage for each internal edges as float from 0 to 0.5
  "connectPt": 0.0, # the position for additional connection edges as float from 0 to 0.5
  "keepDup": false, # whether to keep duplicated edges, which is enssential for blended lattice, which requres multiple different units with same number of edges 
  "filename": "unit_example.obj", # output file name to be saved on server
}
```

Example output:
```python
["unit_example.obj"] # a list of successfully generated file saved on server
```
* <a href='g3doc/installation.md'>live demo</a><br>
<p align="center">
  <img src="imgs/unit.JPG" width=8000>
</p>

### 4. Generate Lattice

Use the API endpoint: https://studiobitonti.appspot.com/boxMorph to assemble lattice units using the conformal grid generated earlier

Example input:
```python
{
  "boxes": "grid_example.json", # name of grid file saved on server
  "component": "unit_example.obj", # name of lattice unit file saved on server
  "filename": "lattice_example.obj",
  "EPSILON": 0.01
}
```

Example output:
```python
["lattice_example.obj"] # a list of successfully generated file saved on server
```
* <a href='g3doc/installation.md'>live demo</a><br>
<p align="center">
  <img src="imgs/lattice.JPG" width=8000>
</p>

### More to come: 

4. Blended lattice

5. Meshing
