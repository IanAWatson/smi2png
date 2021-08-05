# smi2png
Trivial smiles viewer. Uses RDKit to generate a .png depiction, which is sent to eog for viewing.

This is for use at the Linux command line when you want to see a depiction
of the smiles in a file.

# Usage

```
smiles2png file.smi
```
converts the first 30 structures in `file.smi` to png and sends to `eog`.

```
smiles2png -
```
converts the first 30 structures in stdin to png and sends to `eog`.

```
smiles2png --smiles 'CN1C=NC2=C1C(=O)N(C(=O)N2C)C caffeine' --smiles 'c1ccccc1 benzene'
```
smiles strings are passed from the command line.

## Options

- input: Name of smiles file(s) - or use positional arguments (argv)

- smiles: Smiles to be depicted

- n: Number of molecules to display - default 30.

- align: A smiles that is used for aligning the structures.

- mols_per_row: number of molecules per row.

- nrows: number of rows per .png file

- x and -y: dimensions of the .png

- stem: File name stem for the .png files generated.

- verbose: verbose output

- keep: Do NOT remove the .png files after they are shown in `eog`.
