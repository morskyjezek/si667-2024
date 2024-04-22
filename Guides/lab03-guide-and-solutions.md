# Lab 03 - Nature of Digital Content

## Questions and Solutions

1. Note the image files that you choose to work with: choose at least one JPG (extension .jpg or .jpeg) and one TIF (extension .tif or .tiff)
2. Hex editor:
  * Examine the files at the bit level using your hex viewer. Do you notice any similarities or differences? 
  * With special attention to the first bytes of the file, do you notice any similarities with other files of the same type?
  * The first bytes in a file are sometimes a file signature. Can you identify a file signature? [Here is a file signature reference list](https://en.m.wikipedia.org/wiki/List_of_file_signatures)
  * Look for some of the other bit signposts, like `JFIF` in JPG, `0xFFD8` indicates SOI (Start of image), `0xFFDA` indicates SOS (Start of Scan), `0xFFD9` means EOI (End of image).
  * Make modifications using the hex editor. If you have trouble doing this you can also try using the text editor view in VSCode. Delete at least one byte, a section of bytes, or try rearranging bytes. Save the modified file with a new name.
3. Create checksums for the image files.
  * Use `md5` (Mac) or `md5sum` (Windows/GitBash) to create and record the checksum for each of the files.
  * If those tools aren't working for you, try out the Web-based checksum calculator linked above.
  * Goal: a report that lists the MD5 checksum and the file name, separated by a space, on a single line for each file.

4. Compare the checksums of the original and modified files. Are they the same or different?

> One way to compare the strings is to use a command pipeline, for example:
> `md5 -r ecce-homo-half-deleted.jpg ecce-homo-half-deleted.jpg_backup.jpeg | awk '{print $1}' | sort | uniq`
> This pipeline would work on MacOS (use `md5sum` on Windows), or may be adapted to another checksum command.
> **How does it work?**
> * The command generates checksums for the specified files
> * The checksums are printed one on each line to the output
> * The outputs are piped into `awk`, which is useful for parsing columns of text data, in this case the command prints and outputs the first column of the checksum data to the output.
> * Then, those outputs are sorted by `sort`.
> * Finally, the sorted list is filtered to contain only unique values by `uniq`.
> Outcome: If your output has only one line, then there is one unique output, which indicates that the files have the same checksum and are thus identical. If there are two outputs, then there are multiple checksum, which indicates taht the two files are different in some way. 

5. What do you find notable about viewing files in this way? What is the difference between the text files (extensions like: `txt`, `csv`, `md`) and the graphic files (extensions like: `jpg`, `tiff`, `png`)?
  * If you're having trouble getting the hex view, take a look at these examples:
    * A hexdump of a small png file: https://github.com/morskyjezek/si667-2024/blob/main/simplepixel-hexdump
    * The file in the course file collection: https://github.com/morskyjezek/si667-2024/blob/main/simplepixel.pngLinks to an external site.

### BONUS

1. Try reopening any of the graphic files that you edited (tif, png, jpg, etc) with a graphic viewer (like a web browser, Mac Preview, or other program). Can you view the files as graphics? If the files are inaccessible after you edit them, what do you think broke these files? Were there any files/filetypes that didn’t “break” as easily?
1. Post any interesting images that are created in the online discussion.
