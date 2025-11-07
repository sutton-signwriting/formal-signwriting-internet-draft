# The Journey to Formal SignWriting

Sutton SignWriting, recognized under the ISO 15924 script code "Sgnw," is a universal system for writing sign languages.  Formal SignWriting is a digital encoding system I developed to make Sutton SignWriting machine-readable. It includes two encoding forms: Formal SignWriting in ASCII (FSW), stable since 2012, and SignWriting in Unicode (SWU), introduced in 2017.

This journey includes the historical and technical background to the Formal SignWriting standard, outlining the evolution of the encodings I developed over years of effort, from early experiments to these current standards. Valerie Sutton’s foundational work on Sutton SignWriting inspired me, introducing me to the system and its symbols.  But the technical encodings, Formal SignWriting and its predecessors, were entirely my own creations, shaped by personal exploration of character encoding principles. With a consistent vision to make sign languages digitally accessible, I refined each iteration to improve efficiency and utility, preserving all data from the start through careful migration across formats.

My development process was practical: design an encoding, build tools to test it, hit complexity as the code struggled with new demands, refine the encoding to simplify those issues, convert existing data, refactor the tools, and keep building.

This hands-on approach, focused on real-world solutions rather than theory, guided the path to Formal SignWriting: a system now used in education, research, and software worldwide.

---

## Early Conceptualization: The Build String

The journey began with digitizing Sutton SignWriting’s two-dimensional symbol arrangements. Valerie Sutton’s symbol sets, with their six-part IDs (e.g., "01-01-001-01-06-16" for category, group, base, variation, fill, and rotation), were my foundation. I crafted the initial build string to encode these IDs with x, y coordinates in a 250x250 signbox, centered at 125,125 (e.g., "01-01-001-01-06-16,10,20,01-02-002-01-01-01,30,40"). This captured spatial layouts but lacked a one-dimensional order for sorting.

To fix this, I developed build string v2, adding the SignSpelling Sequence (e.g., "01-01-001-01-06-16-01-02-002-01-01-01") to the spatial data. Two-dimensional spaces have no inherent order without a sorting theory: different methods of analysis yield different results. The sequence ensured consistency, enabling practical sorting. Tools built with v2 worked well until larger datasets exposed inefficiencies. I then refined the encoding and migrated all data forward.

---

## Experimental Iterations: Markup, Binary Formats, and Characters

### SignWriting Markup Language - Simple (SWML-Simple)

I then created SignWriting Markup Language - Simple (SWML-Simple), an export option for human-readable markup. It described signs in text but wasn’t suited as the primary encoding. Testing it with tools showed its computational limits, leading me to explore more efficient systems, with data migrated seamlessly.

### Binary SignWriting (BSW)

Binary SignWriting (BSW) was my next step, optimizing encoding through three versions:

- **BSW v1**: Using ISWA 2008, I designed a 16-bit character set with one character per symbol, plus numbers and structural markers. It encoded signs as two-part words (sequence and spatial data). Tools worked until added features slowed them, pushing me to refine further.
    
- **BSW v2**: For ISWA 2010, I switched to a 12-bit set, with each symbol as three hexadecimal characters (e.g., "100"). This boosted precision, but the order of the spatial and sequential data complicated sorting. As tool complexity grew, I adjusted the encoding, converting data to the next version.
    
- **BSW v3**: Keeping the 12-bit set, I moved the sequence to the start. This enabled binary string comparison, simplifying tools significantly.
    

BSW’s evolution showed how I tackled complexity through encoding tweaks, preserving data at each step.

### Character SignWriting (CSW)

Character SignWriting (CSW) mapped BSW v3’s 12-bit characters to Unicode’s Private Use Area on Plane 16, maintaining isomorphism. It aimed for compatibility, and tools performed well until coordinate flexibility became an issue, leading me to the next phase with full data migration.

### Kartesian SignWriting (KSW)

Kartesian SignWriting (KSW) was my design for a lightweight markup with irregular coordinates, centered at 0,0, using "n" for negatives (e.g., "n5x10" for "-5,10"). I offered multiple simultaneous formats:

- **Raw Display Format**: The raw display format string contains the minimal amount of data required to represent text. It defines signs and punctuations. The signboxes are neither centered or sized. A signbox can occur anywhere in the signbox space and the center is not assumed to be the coordinate (0,0). The maximum coordinate for a signbox is unstated. Likewise, the punctuation does not contain any placement information. Layout is impossible without access to an outside datasource.
    
- **Expanded Display Format**: The expanded display format string contains sizing information (width and height) for every symbol outside of the term prefix. The maximum coordinate for a signbox can be calculated by adding the symbol width and height to the symbol placement coordinate. For any symbol key in the signbox or for punctuation, the width and height is accessed from an outside data source. The size information is expressed as an irregular coordinate and appended to each symbol key through a simple search-and-replace process.
    
- **Layout Display Format**: The layout display format string contains the maximum coordinate as a preprocessed value for signboxes and it contains the placement coordinate for punctuation. It is equivalent to the lite markup for the regular searching form, but with irregular coordinates.
    
- **Panel Display Format**: A panel display format string combines multiple signs and punctuations into a unit as a defined height column or defined width row. Each signbox contains an offset coordinate that is used to position the symbols inside of the signbox. The offset is added to the placement coordinate to determine the position of each symbol on the panel. This structure enabled flexible arrangement of signs in rows or columns while maintaining coordinate consistency.
    

KSW’s four-quadrant searching was effective, but irregular coordinates limited precision. As tools hit complexity limits, I progressed, migrating data onward.

---

## The Final Encodings: Formal SignWriting

Formal SignWriting, as I conceived it, took shape with two encoding forms, each refining the digital representation of Sutton SignWriting within its "Sgnw" framework.

Formal SignWriting in ASCII (FSW)

In 2012, I finalized Formal SignWriting in ASCII (FSW), using a 500,500-centered signbox. FSW further reduced complexity by enabling robust two-dimensional searching. All prior data was migrated, ensuring continuity.

SignWriting in Unicode (SWU)

In 2017, I introduced SignWriting in Unicode (SWU), mapping FSW to Unicode code points while preserving isomorphism. SWU enhanced compatibility with modern systems, with data fully transitioned. Since 2012, FSW has been the stable ASCII form of Formal SignWriting, with SWU extending its reach into Unicode in 2017, together rendering earlier formats obsolete.

---

## Impact and Legacy

This journey reflects my work as a lone developer, shaping Formal SignWriting from start to finish through years of persistent effort. Valerie Sutton’s guidance on Sutton SignWriting sparked the process, but the tools, encodings, and technical refinements were my own hands-on work, driven by problem-solving and real-world necessity.

Every iteration preserved the original data through deliberate migration, ensuring nothing was ever lost. In its final forms, Formal SignWriting (FSW) and SignWriting in Unicode (SWU) stand as a complete, stable standard, shared freely through an open Internet-Draft to encourage use without intellectual property restrictions.

I see no need for further revisions. These encodings mark a unique moment in digital writing history. They may one day be superseded, but they will not be replaced. Proven useful and widely adopted, they faithfully embody Valerie Sutton’s vision.  It is a privilege to see them in use.

People apply these standards independently: sometimes asking questions I’m glad to answer, other times surprising me with implementations that inspire awe. Crafted by me, their growth is now beyond my control: a joyful testament to their enduring value.

While my focus was on encoding and tooling, the broader SignWriting community’s creativity and persistence have given these standards life beyond code.

*Author: Steve Slevinski*  
*Date: November 7, 2025*  
*DOI: [10.5281/zenodo.17553763](https://doi.org/10.5281/zenodo.17553763)*

