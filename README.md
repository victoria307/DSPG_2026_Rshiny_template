# R Shiny Project Template

This repository provides a reproducible template for developing and deploying an **R Shiny** application.  
It separates scripts, raw data, cleaned data, and the Shiny app itself for clarity and reproducibility.

---

## 📂 Project Structure

```
shiny-template/
├─ README.md              # Project documentation
├─ .gitignore             # Files ignored by Git
├─ programs/              # Data pipeline scripts
│  ├─ _master.qmd         # The master file to load all the packages, change the directory, and run all the files
│  ├─  cl_00.qmd          # The file changing the format of the file, CSV is more preferred 
|  ├─  cl_01.qmd          # The file that cleans out the relocated observations
|  ├─  cl_02.qmd          # The file that you rename the variables, create the variables you need
|  ├─  cl_03.qmd          # The file that you restrict the sample 
│  └─  an_01.qmd          # The file that you do your first analysis
|
├─ graph/
├─ log/
├─ table/
|  
├─ data/
│  ├─ source/             # Raw Input Dataset
│  └─ outcome/            # Processed outputs from scripts
├─ shiny/                 # Shiny application
│  ├─ app.R
│  ├─ global.R
│  └─ www/                # Static assets (CSS, JS, images)
└─ .github/workflows/     # Optional CI (linting, checks)
```

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/shiny-template.git
cd shiny-template
```

### 2. Install Dependencies
In R, initialize `renv` and install core packages:
```r
install.packages("renv")
renv::init()

# Install essential packages
install.packages(c("shiny", "bslib", "readr", "dplyr", "leaflet", "DT"))
renv::snapshot()
```

### 3. Add Your Data
- Place **raw input data** in `data/raw/` (small, non-sensitive only).  
- Run scripts in `scripts/` to process data into `data/cleaned/`.  

### 4. Run the Shiny App
```r
shiny::runApp("shiny")
```

---

## 📦 Deployment

### shinyapps.io
```r
install.packages("rsconnect")
rsconnect::setAccountInfo(name = "...", token = "...", secret = "...")
rsconnect::deployApp("shiny")
```

### Shiny Server
Copy the `shiny/` folder to your server and configure accordingly.  

---

## 📝 Contributing

- Fork this repository  
- Create a new branch (`git checkout -b feature-new`)  
- Commit your changes (`git commit -m "Add new feature"`)  
- Push to the branch (`git push origin feature-new`)  
- Open a Pull Request  

---

## 📄 License
MIT License – feel free to use, modify, and share.

---

## ⚠️ Notes

- Do **not** commit large or private data to GitHub.  
- Use `.gitignore` to exclude sensitive files.  
- Document how raw data can be obtained in `README_data.md` if applicable.
