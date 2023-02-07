# smi2png

Trivial smiles viewer. Uses RDKit to generate a .png depiction, which is sent
to eog for viewing.

This is for use at the Linux command line when you want to see a depiction of
the smiles in a file.

External dependencies are
+ [RDKit](http://rdkit.org/)
+ [Abseil Python Common Libraries](https://pypi.org/project/absl-py/)
+ [Eye of Gnome (eog)](https://wiki.gnome.org/Apps/EyeOfGnome)

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

- smiles: Smiles to be depicted, can be repeated.

- n: Number of molecules to display - default 30.

- f: If specified, skips the first `f` records in the input.

- align: A smiles that is used for aligning the structures.

- mols_per_row: number of molecules per row (number of columns).

- nrows: number of rows per .png file

- x and -y: dimensions of the .png

- smiles_col: the column in which the smiles is found (def 1)

- id_col: list of columns in which the name is found (def 2)

- sep: the column separator in the input file (def space)

- stem: File name stem for the .png files generated.

- verbose: verbose output

- keep: Do NOT remove the .png files after they are shown in `eog`.

Note that id_col can be a csv list of columns, so if you want to show columns 2
and 3 from a smiles file together with each structure, add `--id_col 2,3`.

Note too that input can be read from sys.stdin. So if you wish to view a
particular record(s) from a smiles file, that can be done with something like
```
grep -E '(CHEMBL224048|CHEMBL449036)' somefile.smi | smiles2png <options>
--input -
```
where `-` is used to signify use of stdin.
