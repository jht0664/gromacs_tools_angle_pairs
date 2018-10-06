# Gromacs_tools_angle_pairs
This is to generate angle and dihedral angles from bond pairs for GROMACS topology files

# Motivation and How to work
As you may know, it is one of tedious works to make topology file for atomistic simulations.
In particular, bond, angle, and dihedral angles (or torsion angles) can count up to few thousand pairs for each molecule.
To reduce cost by typing manually, once we know bond pairs, we can make angles and torsions intuitively, which is very simple.
Based on bond pairs information, we just link connections from bonds, which will be candidates of angles.
And then, just remove duplicates by checking if there is a reverse sequence of a given angle pair.

# Example 
see example/bond.pair;
```
69  # first line is for #atoms
[ bonds ]  # gromacs format to define as bond pairs, but will not read in this script
; ai  aj  funct # comment line in gromacs format, which will not read
 1   2   1 # atom index 1 and index 2 are connected with bond. Third column will be ignored for reading
 2   3   1 
 3   4   1
 3   5   1
 3   6   1
 ```
 when you type in command line, `python -i gen-ang-dih.py -o ang-dih.pair`, the output file `ang-dih.apri` comes out.
 
 # Limitation
 This works even with ring structure molecules.
 This program does not support making improper torsion angles, which you need to make manually.
 
