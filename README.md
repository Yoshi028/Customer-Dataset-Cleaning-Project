# Customer-Dataset-Cleaning-Project

This project demonstrates a complete data cleaning workflow using **Excel Power Query**.  
The raw dataset contained multiple inconsistencies such as missing values, formatting errors, duplicated rows, and mixed data types.  
The goal of this project is to prepare a clean, standardized dataset that is suitable for analysis and reporting.

---

## 📌 Project Overview
**File cleaned:** `customers.csv`  
**Rows:** 20  
**Columns:**  
- CustomerID  
- First_Name  
- Last_Name  
- Phone_Number  
- Address  
- Paying Customer  
- Do_Not_Contact  
- Not_Useful_Column  

---

## 🔍 Data Quality Issues Found
The raw data included the following common problems:

### **1. Missing or incomplete fields**
- `Last_Name` missing in 1 row  
- `Phone_Number` missing in 4 rows  
- `Paying Customer` missing in 1 row  
- `Do_Not_Contact` missing in 4 rows  
- Address included 1 `"Unknown"` entry  
- Multiple `N/a` values

---

### **2. Inconsistent formatting**
- Phone numbers in different formats:
  - `123-545-5421`
  - `123/643/9775`
  - `876|678|3469`
  - `7066950392`
- Last names with unwanted characters:
  - `/White`
  - `...Potter`
  - `Flenderson_`
  - `"  Winger"` (leading spaces)

---

### **3. Mixed data types**
- `Paying Customer` included: `Yes`, `No`, `Y`, `N`
- `Do_Not_Contact` included: `Yes`, `No`, `Y`, `N`, blanks
- Phone number column contained text like: `"N/a"`

---

### **4. Duplicated rows**
- CustomerID **1020** appeared twice with identical data.

---

### **5. Unnecessary column**
- `Not_Useful_Column` contained only boolean-like values and served no analytical purpose.

---

## 🛠 Cleaning Steps Performed (Power Query)

### **1. Trimmed and cleaned names**
- Removed leading/trailing spaces  
- Used `Text.Proper()` to normalize capitalization  
- Removed symbols (`/`, `_`, `...`)  
- Corrected rows such as:
  - `/White` → `White`
  - `...Potter` → `Potter`
  - `Flenderson_` → `Flenderson`
  - `  Winger` → `Winger`

---

### **2. Standardized phone numbers**
Steps included:
- Removed all non-numeric characters using:  
Text.Select([Phone_Number], {"0".."9"})

- Reformatted to a consistent format:  
`1235455421` → `123-545-5421`
- Replaced invalid values (`"N/a"`) → **Unknown**

---

### **3. Cleaned Address**
- `"N/a"` → **null**
- Retained addresses where formatting was correct

---

### **4. Normalized categorical fields**
Converted all values to a standard format:

#### **Paying Customer**
| Raw values | Standard value |
|-----------|----------------|
| Yes, Y | Yes |
| No, N | No |
| blank | Unknown |

#### **Do_Not_Contact**
| Raw values | Standard value |
|-----------|----------------|
| Yes, Y | Yes |
| No, N | No |
| blank | Unknown |

---

### **5. Removed duplicate rows**
- Removed duplicate **CustomerID 1020**
- Kept only the first occurrence

---

### **6. Removed unnecessary column**
- Deleted `Not_Useful_Column`

---

## ✅ Final Output
**A fully cleaned and standardized dataset** suitable for:  
- Customer segmentation  
- CRM analytics  
- Contact list validation  
- Visualization reporting  
- Machine learning preprocessing

---

## 📂 Project Structure
├── data/  
│ ├── customers_raw.csv  
│ ├── customers_clean.csv  
└── README.md  


---

## 📊 Skills Demonstrated
- Power Query M-language transformation  
- Data cleaning best practices  
- Handling missing data  
- String manipulation  
- Removing duplicates  
- Converting inconsistent categorical values  
- Documentation for analytics projects
