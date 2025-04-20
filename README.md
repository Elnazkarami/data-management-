# Data Restructuring Tool

This tool is designed to read compressed files and restructure the extracted data into a specific directory structure. It is specifically tailored for data from the Miniscope project, but can be adapted for other datasets with similar organizational needs.

## Purpose

The purpose of this tool is to automate the process of organizing raw data from compressed archives into a standardized directory structure, making it easier to analyze and process the data.

## Directory Structure

The tool restructures the data into the following directory structure:

```
output/
  raw_data/
    Session_Date/
      Subject_ID/
        Session_ID/
          raw/
            [Data files]
```

Where:

*   `output` is the main output directory (specified as a command-line argument).
*   `Session_Date`, `Subject_ID`, and `Session_ID` are extracted from the input file path.
*   `raw` is a subdirectory containing the raw data files.

## Usage

1.  **Install Dependencies:**

    This tool requires Python 3 and the following packages:

    *   `zipfile`
    *   `tarfile`
    *   `gzip`
    *   `bz2`
    *   `os`
    *   `shutil`

    You can install these packages using pip:

    ```bash
    pip3 install shutil
    ```

2.  **Run the Script:**

    To run the script, use the following command:

    ```bash
    python3 read_compressed.py <target_directory>
    ```

    Where `<target_directory>` is the directory containing the compressed files you want to process.

## Script Details

*   `read_compressed.py`: The main script that handles the overall workflow.
*   `compression_handler.py`: Handles the extraction of compressed files.
*   `data_extractor.py`: Identifies the file types.
*   `data_restructurer.py`: Creates the directory structure and moves the files.
*   `error_handler.py`: Handles errors and logs them.

## Supported File Types

The tool currently supports the following file types:

*   `.txt`
*   `.csv`
*   `.json`
*   `.npy`
*   `.mat`
*   `.dat`
*   `.avi`
*   `.rhd`
*   `.pkl`
*   `.npz`
*   `.h5`
*   `.hdf5`
*   `.nev`
*   `.nsx`
*   `.ncs`
*   `.edf`
*   `.tdt`
*   `.kwik`
*   `.phy`
*   `.kilo`
*   `.bin`
*   `.yaml`
*   `.ini`
*   `.m`
*   `.sh`
*   `.bash`
*   `.r`
*   `.md`

## Notes

*   The script skips `.DS_Store` files.
*   The script skips the move operation if the destination file already exists.
*   The script assumes that the input file path contains the session date, subject ID, and session ID in the following format: `.../Session_Date/Subject_ID/Session_ID/...`

## Example

To process the compressed files in the directory `/Users/Data /miniscope /AXXXX/AXXXX`, you would run the following command:

```bash
python3 read_compressed.py "/Users/Data /miniscope /AXXXX/AXXXX"
