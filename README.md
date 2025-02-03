# miRNA Extraction

`optimized-miRNA-extraction-logs` is an optimized pipeline for downloading, processing, and extracting data from miRNA-related sources. This script supports multi-threaded downloads, batch processing, and detailed logging for debugging and analysis.

## Features
- **Multi-threaded Downloading**: Uses `ThreadPoolExecutor` for concurrent miRNA file downloads.
- **Error Handling & Logging**: Implements retries for failed downloads and logs execution details using `RotatingFileHandler`.
- **Parallel Data Extraction**: Processes files in batches to improve efficiency.
- **Filtering Mechanism**: Excludes rows with `type=lncRNA` to retain only relevant miRNA data.
- **Structured Output Files**: Saves results into categorized CSV files.

## How It Works
1. **Batch Downloading**
   - Reads miRNA names from an Excel file.
   - Downloads data from [miRBase](https://rnasysu.com/encori/index.php) with retry mechanisms.
2. **File Processing & Extraction**
   - Validates and extracts relevant miRNA data from downloaded files.
   - Filters out rows with `type=lncRNA`(can be changed as per requirement) and removes files with "No Available results".
3. **Logging & Error Tracking**
   - Maintains logs for downloads, processing, and errors.
   - Generates structured output files for analysis.

## Output Files
Processed data is stored in the `output/` directory:
- `extracted_data_final.csv` - Consolidated extracted data.
- `not_downloaded_final.csv` - Files that failed to download.
- `error_files_final.csv` - Files with processing errors.
- `data_not_found_final.csv` - Files containing no relevant data.

## Running the Script
Execute the script using:
```python
download_and_process_mirna(
    'data.xlsx',
    batch_size=50,
    download_workers=8,  
    process_workers=4    
)
```
This will start the download and extraction process while logging execution details.

## Variants
- **optimized-miRNA-extraction**: Identical to `optimized-miRNA-extraction-logs`, but without logging.
- **miRNA-extraction**: A basic version without logging or multi-threading.

