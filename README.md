# shoemaster_example

The Conformal Lattice example requires few API calls to be accomplished.

Step 1. Prepare point grid in specific order from 4 surrounding surfaces.

[DIAGRAM HERE]

Step 2. Use /conformalGrid function to construct a list of box-shaped scaffold.

Step 3. Use /latticeUnit function to generate a parametrically described lattice unit

Step 4. Use /boxMorph function to assemble lattice units using the box scaffold generated earlier

OPTION. Blended lattice using point/vector/curve attractors

Step 5. Use /marchineCube function to generate 3D-printable stl files