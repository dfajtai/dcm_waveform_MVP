# dcm2waveform_MVP

**A lightweight Python project (MVP) designed to extract waveforms from DICOM images, leveraging publicly available Python libraries. This release focuses solely on core functionalities, offering no insight into the advanced, high-level implementations beyond this foundational scope - for those who prefer not to reinvent the wheel or spend two minutes searching for solutions themselves.**

---

## ⚠️ Warning

**Please note:** This code does not handle GDPR compliance or modern data privacy policies. The extracted results are stored in simple JSON/YAML and CSV formats, with **no anonymization** or data protection features implemented. Use this tool responsibly and ensure that you comply with relevant data privacy regulations when working with sensitive information.

---

## Sample Data Source

This project uses sample DICOM ECG data from the [marcodebe/dicom-ecg-plot](https://github.com/marcodebe/dicom-ecg-plot) repository. The repository provides tools for plotting ECG waveforms from DICOM files and includes sample data for testing and demonstration purposes.

---

## Additional Resources

For further reading and understanding of DICOM waveforms and their handling in Python, check out the following resources:

- [DICOM Waveform Standard (Supplement 30)](https://www.dicomstandard.org/News-dir/ftsup/docs/sups/sup30.pdf): Detailed documentation about the DICOM waveform standard.
- [Innolitics - DICOM Standard Browser](https://dicom.innolitics.com/ciods/electrooculogram/waveform/54000100): Structured, detailed references.
- [Pydicom Waveform Tutorial](https://pydicom.github.io/pydicom/dev/tutorials/waveforms.html): A tutorial on working with waveform data in DICOM files using the `pydicom` library.

---

## Build

To build the project into a standalone executable, use the provided installer scripts. These scripts handle everything, including cleaning previous builds, installing dependencies, and creating the executable.

### **For Linux**

Run the following command to build the project:

```
./installer/build.sh
```

### **For Windows**

Run the following command in Command Prompt to build the project:

```
installer\build.bat
```

### **Output**

The resulting executable will be located in the `dist/` folder:

- On Linux: `dist/main`
- On Windows: `dist\main.exe`

---

## Usage

The generated executable can be used to process DICOM files, extract waveform data, and save the results as CSV files along with metadata in JSON or YAML format. The executable supports various command-line arguments for flexibility.

### **Basic Usage**

Run the executable without any arguments to use the default configuration (`config.json`):

- Linux/MacOS: `./main`
- Windows: `main.exe`

### **Command-Line Arguments**

| Argument             | Description                                                                                  | Example                                                                 |
| -------------------- | -------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `--config`           | Path to the configuration file (default: `./config.json`).                                   | `--config ./custom_config.json`                                         |
| `--input_dir`        | Override the input directory specified in the config file.                                   | `--input_dir ./my_dicom_files`                                          |
| `--output_dir`       | Override the output directory specified in the config file.                                  | `--output_dir ./my_output_folder`                                       |
| `--metadata_format`  | Override the metadata format specified in the config file (`json` or `yaml`).                | `--metadata_format yaml`                                                |
| `--output_structure` | Override the output folder structure using placeholders like `{PATIENT_ID}/{STUDY_DATE}`.    | `--output_structure "{PATIENT_ID}/{STUDY_DATE}/{STUDY_TIME}/{CHANNEL}"` |
| `--file_format_mask` | Override the file format mask specified in the config file (e.g., `*.dcm`, `*.ima`, or `*`). | `--file_format_mask "*.dcm" "*.ima"`                                    |

### **Examples**

1. **Using Default Configuration**  
   Run the executable with default settings from `config.json`:

   - Linux/MacOS: `./main`
   - Windows: `main.exe`

2. **Specifying a Custom Input Directory**  
   Override the input directory to process DICOM files from a different folder:  
   `./main --input_dir ./custom_dicom_files`

3. **Changing Output Directory**  
   Save results to a custom output folder:  
   `./main --output_dir ./custom_output_folder`

4. **Changing Metadata Format**  
   Save metadata in YAML format instead of JSON:  
   `./main --metadata_format yaml`

5. **Customizing Output Folder Structure**  
   Organize output files using a custom folder structure:  
   `./main --output_structure "{PATIENT_ID}/{ACCESSION_NUMBER}/{STUDY_DATE}/{CHANNEL}"`

6. **Using a Custom File Format Mask**  
   Process files with `.dcm`, `.ima`, or no extension:  
   `./main --file_format_mask "*.dcm" "*.ima" "*"`

7. **Combining Multiple Options**  
   You can combine multiple arguments for full customization:

```
./main --config ./custom_config.json
--input_dir ./my_dicom_files
--output_dir ./my_output_folder
--metadata_format yaml
--output_structure "{PATIENT_ID}/{STUDY_DATE}/{CHANNEL}"
--file_format_mask ".dcm" ".ima"
```

### **Error Logging**

- Errors encountered during execution are logged to an `error.log` file located in the same directory as the executable.
- Check this file for detailed error messages and troubleshooting.

### **Output**

- Processed waveform data is saved as CSV files in the specified output directory.
- Metadata is saved as JSON or YAML files based on your configuration.
