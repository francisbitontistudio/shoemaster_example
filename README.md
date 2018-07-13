# shoemaster_example

The Conformal Lattice example requires few API calls to be accomplished.

### 1. Export Surface Grid

[DIAGRAM HERE]



### 2. Create Conformal Grid

Use the API endpoint: https://studiobitonti.appspot.com/conformalGrid to construct a list of box-shaped scaffold.

Example input:
```python
{
  "u":40, # how many time to divide the surfaces in each direction 
  "v":8,
  "w":4, 
  "surfaces": "sole.json",  # the name of json file on server representing the surfaces
  "filename": "grid.json",  # the name output grid file
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

Use the endpoint /latticeUnit function to generate a parametrically described lattice unit

<p align="center">
  <img src="imgs/unit.JPG" width=8000>
</p>

### 4. Generate Lattice

Use /boxMorph function to assemble lattice units using the box scaffold generated earlier

<p align="center">
  <img src="imgs/lattice.JPG" width=8000>
</p>

OPTION. Blended lattice using point/vector/curve attractors

### Step 5. Meshing
Use /marchineCube function to generate 3D-printable stl files
