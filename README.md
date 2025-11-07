# Formal SignWriting

This repository hosts the source XML and generated documents for the "Formal SignWriting" IETF draft standard (draft-slevinski-formal-signwriting).  This document specifies the Formal SignWriting character sets, grammar, token patterns, symbol encoding, spatial organization, and sequence representation. It also details technical integration for both Formal SignWriting in ASCII (FSW) and SignWriting in Unicode (SWU) formats, including styling string, query languages, and transformations.

## Background
For an overview of the standard's origins, development history, and relation to Sutton SignWriting, see [background.md](background.md).

## Directory Structure
- **`source/`**: Contains the source XML files for all revisions of Formal SignWriting.
- **`dist/`**: Pre-generated HTML, TXT, and PDF versions of the latest revision ready for distribution.
- **`background.md`**: Explanatory document on the standard's background.
- **`CITATION.cff`**: Metadata for citing this repository (see "Citation" section below).
- **`LICENSE`**: Terms for use and distribution.

## Generating Documents
To generate HTML, TXT, or PDF from any XML source:
1. Visit the IETF Author Tools: [https://author-tools.ietf.org/](https://author-tools.ietf.org/).
2. Upload the desired XML file (e.g., from `/source/`).
3. Select the output format and download.

This ensures consistency with IETF formatting standards.

## Citation
To cite this draft, use the information in [CITATION.cff](CITATION.cff). GitHub provides a "Cite this repository" feature based on this file.

This draft has been published on Zenodo with DOI: [https://doi.org/10.5281/zenodo.17553763](https://doi.org/10.5281/zenodo.17553763).

## Contributing
Contributions are welcome for corrections, clarifications, or extensions to the standard. Please open an issue or pull request. For major changes, discuss in an issue first.

## Related Resources
Part of the broader Sutton SignWriting effort:
- GitHub Organization: [https://github.com/sutton-signwriting](https://github.com/sutton-signwriting)
- Website: [https://www.sutton-signwriting.io/](https://www.sutton-signwriting.io/)

## License
This project is licensed under the Creative Commons Attribution 4.0 International License (CC-BY-4.0).
