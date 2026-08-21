<div align="center">

# 🎓 Student Performance — Calculative Foundation

### 🧮 Linear Algebra • 📊 Data Analysis • 🐍 Python • 📈 PCA

A practical Python project that applies **vector & matrix mathematics, linear algebra, eigenvalues, eigenvectors and PCA-style dimensionality reduction** to student performance data.

<br/>

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![NumPy](https://img.shields.io/badge/NumPy-Linear%20Algebra-013243?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=for-the-badge)](https://matplotlib.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)

<br/>

**📌 Academic Project | Data Analysis + Mathematical Computing**

</div>

---

## 🚀 Quick Navigation

| 🔗 Section | 🔗 Section |
|---|---|
| [📖 About](#-about-the-project) | [🎯 Objectives](#-project-objectives) |
| [📊 Dataset](#-dataset) | [🧰 Tech Stack](#-technology-stack) |
| [🧮 Concepts](#-core-concepts) | [📈 PCA](#-pca-style-dimensionality-reduction) |
| [⚙️ Installation](#️-installation) | [▶️ Run](#️-how-to-run) |
| [⚠️ Compatibility](#️-important-compatibility-note) | [🔮 Future](#-future-improvements) |

---

# 📖 About the Project

This project explores **student academic performance through the lens of linear algebra and numerical computing**.

The supplied Jupyter Notebook loads student performance data and transforms subject scores into numerical vectors and matrices. It then performs vector operations, matrix operations, covariance/eigenvalue analysis and a PCA-style 2D projection. fileciteturn1file0L17-L33 fileciteturn1file0L40-L84

> 💡 **Why this project?**  
> It connects mathematical foundations with a practical dataset, showing how concepts from linear algebra can be implemented using Python.

---

# 🎯 Project Objectives

### 🧮 Mathematical Computing
- Calculate **Norm-1 and Norm-2**
- Calculate **Dot Product**
- Calculate the **angle between vectors**
- Calculate the **Cross Product**
- Calculate **Vector Projection**
- Perform **Matrix Addition**
- Calculate **Matrix Transpose**
- Perform **Matrix Multiplication**
- Calculate **Determinant**
- Calculate **Matrix Inverse**

### 📊 Data & Statistics
- Load CSV data with Pandas
- Convert subject scores into numerical arrays
- Calculate the covariance matrix
- Calculate eigenvalues and eigenvectors
- Calculate explained variance

### 📉 Dimensionality Reduction
- Center the dataset
- Project four-dimensional data onto the first two principal components
- Visualize students in a **2D PCA-style scatter plot**

These operations are implemented in the supplied notebook. fileciteturn1file0L92-L176 fileciteturn1file0L184-L269 fileciteturn1file0L298-L368

---

# 📂 Project Structure

```text
📦 Student-Performance-Calculative-Foundation
│
├── 📓 PR4_Calculative_Foundation_Solution.ipynb
├── 📊 student_performance.csv
└── 📄 README.md
```

---

# 📊 Dataset

The supplied CSV contains **8 student records** with these columns: fileciteturn1file1L396-L404

| Column | Meaning |
|---|---|
| 👤 `Student` | Student identifier |
| 🧮 `Mathematics` | Mathematics score |
| ⚛️ `Physics` | Physics score |
| 🧪 `Chemistry` | Chemistry score |
| 💻 `Computer` | Computer-related score |

### 📌 Sample Records

| Student | Mathematics | Physics | Chemistry | Computer |
|---|---:|---:|---:|---:|
| S01 | 78 | 82 | 75 | 88 |
| S02 | 65 | 70 | 68 | 74 |
| S03 | 88 | 85 | 90 | 92 |
| S04 | 72 | 68 | 70 | 76 |
| S05 | 91 | 94 | 89 | 96 |
| S06 | 60 | 63 | 61 | 69 |
| S07 | 84 | 80 | 86 | 90 |
| S08 | 75 | 77 | 73 | 81 |

Source: supplied `student_performance.csv`. fileciteturn1file1L396-L404

---

# 🧰 Technology Stack

<div align="center">

| Technology | Purpose |
|---|---|
| 🐍 **Python** | Core programming language |
| 🔢 **NumPy** | Vectors, matrices & numerical calculations |
| 🐼 **Pandas** | Dataset loading & DataFrame operations |
| 📈 **Matplotlib** | Data visualization |
| 📓 **Jupyter Notebook** | Interactive project environment |

</div>

The notebook imports NumPy, Pandas and Matplotlib and reads the dataset with `pd.read_csv()`. fileciteturn1file0L21-L33

---

# 🧮 Core Concepts

## 1️⃣ Vector Representation

Student subject scores are represented as numerical vectors.

```python
X = df[[
    "Mathematics",
    "Physics",
    "Computer Science",
    "Statistics"
]].to_numpy(dtype=float)
```

This representation is then used for the vector and matrix calculations in the notebook. fileciteturn1file0L49-L55

---

## 2️⃣ 📏 Norm-1 & Norm-2

The project calculates two vector magnitudes:

```python
norm1 = np.sum(np.abs(X), axis=1)
norm2 = np.linalg.norm(X, axis=1)
```

- **Norm-1** → sum of absolute values
- **Norm-2** → Euclidean vector magnitude

The notebook interprets larger values as a larger overall score-vector magnitude. fileciteturn1file0L62-L84

---

## 3️⃣ 🔗 Dot Product & Angle

The project calculates the dot product between two selected student vectors and derives the angle between them.

```python
dot = np.dot(v1, v2)

angle = np.degrees(
    np.arccos(
        dot / (np.linalg.norm(v1) * np.linalg.norm(v2))
    )
)
```

A smaller angle indicates more similar direction between the two performance vectors. fileciteturn1file0L92-L116

---

## 4️⃣ ✖️ Cross Product

For selected 3D score vectors, the notebook calculates:

```python
cross = np.cross(a3, b3)
```

It also checks perpendicularity using dot products with the resulting cross-product vector. fileciteturn1file0L124-L149

---

## 5️⃣ 📐 Vector Projection

The notebook calculates the projection of one student's score vector onto another student's vector:

```python
projection = (
    np.dot(v1, v2) / np.dot(v2, v2)
) * v2
```

This represents the component of one score vector lying in the direction of another. fileciteturn1file0L157-L176

---

# 🧱 Matrix Operations

## ➕ Matrix Addition

The project demonstrates element-wise matrix addition:

```python
M + M
```

## 🔄 Matrix Transpose

```python
M.T
```

Transpose swaps the rows and columns of the matrix. fileciteturn1file0L184-L208

---

## ✖️ Matrix Multiplication

The notebook calculates:

```python
ATA = X.T @ X
```

`XᵀX` produces a matrix capturing pairwise products among the subject-score columns and is useful in linear-algebra calculations. fileciteturn1file0L216-L236

---

## 🔢 Determinant & Inverse

The project calculates:

```python
det_M = np.linalg.det(M)
inv_M = np.linalg.inv(M)
```

It then verifies the inverse using:

```python
M @ inv_M
```

The notebook notes that the result is approximately the identity matrix because of floating-point precision. fileciteturn1file0L244-L269

---

# 📐 Linear Transformations & Geometry

The notebook demonstrates the same student's scores in different dimensions:

```text
2D → Mathematics + Physics
3D → Mathematics + Physics + Computer Science
4D → Mathematics + Physics + Computer Science + Statistics
```

This provides a simple illustration of dimensional representation. fileciteturn1file0L277-L290

---

# 🧬 Eigenvalues & Eigenvectors

The project calculates the covariance matrix:

```python
cov = np.cov(X, rowvar=False)
```

Then obtains eigenvalues and eigenvectors:

```python
eigvals, eigvecs = np.linalg.eigh(cov)
```

The eigenvalues are sorted from largest to smallest and converted into explained-variance percentages. fileciteturn1file0L298-L330

### 🧠 Interpretation

> The largest eigenvalue represents the principal direction capturing the greatest amount of variance in the data.

---

# 📉 PCA-Style Dimensionality Reduction

One of the key parts of the project is reducing the original four-dimensional student data into a two-dimensional representation.

### 🔹 Step 1 — Center the Data

```python
X_centered = X - X.mean(axis=0)
```

### 🔹 Step 2 — Select First Two Eigenvectors

```python
eigvecs[:, :2]
```

### 🔹 Step 3 — Calculate 2D Scores

```python
scores2 = X_centered @ eigvecs[:, :2]
```

### 🔹 Step 4 — Visualize

The notebook creates a scatter plot using:

- `PC1` → Principal Component 1
- `PC2` → Principal Component 2

Each student is annotated on the plot. fileciteturn1file0L338-L368

---

# 📈 Visualization

### 📊 Student Performance — First Two Principal Components

The resulting visualization provides a compact 2D representation of the students after projecting the original data onto the first two principal directions. fileciteturn1file0L351-L368

```text
Original Data
     │
     ▼
4-D Student Performance
     │
     ▼
Center Data
     │
     ▼
Covariance Matrix
     │
     ▼
Eigenvalues + Eigenvectors
     │
     ▼
Select PC1 + PC2
     │
     ▼
📈 2-D Visualization
```

---

# ⚙️ Installation

## 1. Clone the Repository

```bash
git clone <YOUR-GITHUB-REPOSITORY-URL>
cd Student-Performance-Calculative-Foundation
```

## 2. Install Dependencies

```bash
pip install numpy pandas matplotlib jupyter
```

## 3. Start Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```text
PR4_Calculative_Foundation_Solution.ipynb
```

---

# ▶️ How to Run

### Step 1
📥 Download/clone the project.

### Step 2
📁 Keep these files in the same folder:

```text
📓 PR4_Calculative_Foundation_Solution.ipynb
📊 student_performance.csv
```

### Step 3
🚀 Start Jupyter Notebook.

### Step 4
📓 Open the `.ipynb` file.

### Step 5
▶️ Run the cells from top to bottom.

---

# ⚠️ Important Compatibility Note

There is an **actual column-name mismatch** between the supplied CSV and notebook.

### CSV columns

```text
Student
Mathematics
Physics
Chemistry
Computer
```

### Notebook-selected columns

```text
Mathematics
Physics
Computer Science
Statistics
```

The notebook explicitly selects `Computer Science` and `Statistics`, while the supplied CSV contains `Chemistry` and `Computer`. fileciteturn1file0L49-L55 fileciteturn1file1L396-L404

Therefore, the notebook should be aligned with the actual CSV column names before execution.

> 🟡 **Note:** This README documents the supplied files as they are and does not silently modify the original project.

---

# 📚 What I Learned

Through this project, the following concepts are demonstrated:

- 🐍 Python programming
- 🐼 Pandas DataFrame handling
- 🔢 NumPy arrays
- 📏 Vector norms
- 🔗 Dot products
- ✖️ Cross products
- 📐 Vector projection
- 🧱 Matrix operations
- 🔄 Matrix transpose
- ✖️ Matrix multiplication
- 🔢 Determinant & inverse
- 📊 Covariance
- 🧬 Eigenvalues & eigenvectors
- 📉 PCA concepts
- 📈 Data visualization
- 🧠 Mathematical thinking for data analysis

---

# 🔮 Future Improvements

- [ ] 📊 Add subject-wise performance charts
- [ ] 📈 Add correlation analysis
- [ ] 🏆 Add student ranking
- [ ] 🧮 Add overall score calculation
- [ ] 📊 Add descriptive statistics
- [ ] 📈 Add more PCA visualizations
- [ ] 📂 Use a larger student dataset
- [ ] 🎨 Build an interactive dashboard
- [ ] ⚡ Add automated data validation
- [ ] 📱 Create a web-based student analytics application

---

# 🏆 Project Highlights

<div align="center">

| ⭐ Feature | Status |
|---|---|
| 🐍 Python Implementation | ✅ |
| 📊 CSV Data Analysis | ✅ |
| 🧮 Vector Operations | ✅ |
| 🧱 Matrix Operations | ✅ |
| 🧬 Eigenvalue Analysis | ✅ |
| 📉 PCA-Style Reduction | ✅ |
| 📈 Visualization | ✅ |
| 📓 Jupyter Notebook | ✅ |

</div>

---

# 👨‍💻 Author

<div align="center">

### **Indrajeet Maheshwari**

🎯 **Aspiring Data Analyst**

💡 Interested in **Data Analysis • Python • SQL • Visualization • Machine Learning**

</div>

---

# ⭐ Support

If you found this project useful:

⭐ **Star the repository**  
🍴 **Fork the project**  
📢 **Share it with others**  
💬 **Give feedback**

---

<div align="center">

### 🚀 Built with Python & Mathematical Thinking

**From Student Scores → Vectors → Matrices → Eigenvectors → PCA → Visualization**

<br/>

[⬆️ Back to Top](#-student-performance--calculative-foundation)

</div>
