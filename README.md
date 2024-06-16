# ArXiv Paper Downloader

這個Python程式可以自動從arXiv下載關於特定主題的論文，使用者可以指定搜尋多個關鍵詞、論文上傳年月範圍和下載的論文數量，以下有中英文的說明。

This Python program can automatically download papers from arXiv based on specific keywords (multiple keywords are supported), the range of publication year-month, and the desired number of papers to download. Below are introductions and instructions in both Chinese and English.

- [中文介紹](#功能特點)
- [English Introductions](#feature-highlights)


-----------

## 功能特點

- **關鍵詞搜索**: 根據用戶提供的關鍵詞進行論文搜索，支援多個關鍵字輸入。
- **日期範圍設定**: 用戶可以指定搜尋的論文上傳年月區間。
- **自動下載**: 程式會自動下載搜索結果中的論文至本機特定資料夾。
- **避免重複下載**: 將已下載的論文資訊維護在excel裡，供後續查看以及避免重複下載。

## 安裝需求

請確保您的系統已經安裝了以下Python套件：

- pandas
- requests
- beautifulsoup4
- selenium

您可以使用以下命令安裝這些套件：

```bash
pip install pandas requests beautifulsoup4 selenium
```

## 使用方法

以下說明為Windows用戶舉例：

1. **Clone或下載本程式到您的電腦**

1. **開啟命令提示字元(cmd)或 PowerShell**：
   - 按下 `Win` 鍵，然後在搜索框中輸入 "cmd" 或 "PowerShell"，選擇相應的程式來開啟。

2. **導航到您的Python程式所在的目錄**：
   - 使用 `cd` 命令改變當前目錄到程式所在的位置。例如，如果您的 `main.py` 文件在 `C:\Users\Username\Documents\Project` 目錄下，您可以輸入：
     ```bash
     cd C:\Users\Username\Documents\Project
     ```

3. **執行程式**：
   - 在命令行中輸入以下命令，確保替換中括號內的參數為您的需求設置：
     ```bash
     python main.py --queries [關鍵詞] --start_year_month [起始年月] --end_year_month [結束年月] --num_papers [下載數量]
     ```
    - 例如，要下載關於 "fairness", "machine learning" 和 "synthetic data generation" 的論文，並設定搜索時間範圍從 2023 年 1 月到 2023 年 12 月，可以使用以下命令：
     ```bash
     python main.py --queries "fairness" "machine learning" "synthetic data generation" --start_year_month 202301 --end_year_month 202312 --num_papers 5
     ```

請確保您的系統已經安裝Python和必要的套件，如[安裝需求](#安裝需求)部分所述。

## 設定參數預設值

本程式支持設置預設參數值，讓使用者在不指定命令行參數時，可以自動使用預設的搜索設定，對於常用相同參數的使用者來說較為方便。

#### 預設值設定

以下是 `Config` 類別的實現，它在程式中被用來儲存所有預設的參數：

```python
class Config:
    DEFAULT_QUERIES = ["fairness", "machine learning", "synthetic data generation"]
    DEFAULT_START_YEAR_MONTH = "202301"
    DEFAULT_END_YEAR_MONTH = "202312"
    DEFAULT_NUM_PAPERS = 5
```

#### 使用預設值

當您在命令行中不指定對應的參數時，程式將會自動使用 `Config` 類別中定義的預設值。並且如果您僅指定部分參數，其他未指定的參數也會使用這些預設值。

#### 修改預設值

要修改這些預設值，您可以直接在 `Config` 類別中進行更改。這樣做可以讓程式更靈活地符合您的特定需求，無需在每次執行時手動輸入所有參數，以簡化常規操作。

-----------

## Feature Highlights

- **Keywords Search**: Conducts paper searches based on keywords provided by the user, supporting multiple keyword entries.
- **Paper Upload Date Range Setting**: Users can specify the year-month range for the paper uploaded date they wish to search.
- **Automatic Download**: The program automatically downloads the search results to a specific local folder.
- **Avoid Duplicate Downloads**: Records information about downloaded papers in an Excel file for future reference and to prevent duplicate downloads.

## Installation Requirements

Please ensure your system has the following Python packages installed:

- pandas
- requests
- beautifulsoup4
- selenium

You can install these packages using the following command:

```bash
pip install pandas requests beautifulsoup4 selenium
```

## User Instructions

The following instructions are intended for Windows users:

1. **Clone or download the program to your computer**

2. **Open Command Prompt (cmd) or PowerShell**:
   - Press the `Win` key, then type "cmd" or "PowerShell" in the search box and select the appropriate program to open.

3. **Navigate to the directory containing your Python program**:
   - Use the `cd` command to change to the directory where your `main.py` file is located. For example, if your `main.py` file is in `C:\Users\Username\Documents\Project`, you can enter:
     ```bash
     cd C:\Users\Username\Documents\Project
     ```

4. **Execute the program**:
   - Enter the following command in the command line, ensuring to replace the parameters in brackets with your specified settings:
     ```bash
     python main.py --queries [keywords] --start_year_month [start year-month] --end_year_month [end year-month] --num_papers [number of papers]
     ```
   - For example, to download papers on "fairness", "machine learning", and "synthetic data generation", and to set the search time period between January 2023 and December 2023, you can use the following command:
     ```bash
     python main.py --queries "fairness" "machine learning" "synthetic data generation" --start_year_month 202301 --end_year_month 202312 --num_papers 5
     ```

Please ensure your system has Python and the necessary packages installed, as outlined in the [Installation Requirements](#installation-requirements) section.

## Setting Default Parameters

This program supports setting default parameter values, allowing users to automatically use predefined search settings when no command line parameters are specified. This feature is convenient for users who frequently use the same parameters.

#### Default Value Settings

Below is the implementation of the `Config` class, which is used in the program to store all default parameters:

```python
class Config:
    DEFAULT_QUERIES = ["fairness", "machine learning", "synthetic data generation"]
    DEFAULT_START_YEAR_MONTH = "202301"
    DEFAULT_END_YEAR_MONTH = "202312"
    DEFAULT_NUM_PAPERS = 5
```

#### Using Default Values

When you do not specify corresponding parameters in the command line, the program will automatically use the default values defined in the `Config` class. Additionally, if you only specify some parameters, the other unspecified parameters will also default to these preset values.

#### Modifying Default Values

To modify these default values, you can directly edit them in the `Config` class. This flexibility allows the program to better adapt to your specific needs without the need to manually enter all parameters each time you run it, thus simplifying routine operations.
