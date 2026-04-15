[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23572368&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student ID:** 2A202600138
**Name:** Nguyen Binh Thanh

---

## Mo ta

Bai lab xay dung mot ETL pipeline tu dong de xu ly du lieu san pham tu file JSON. Pipeline thuc hien 4 buoc: Extract du lieu tu file JSON, Validate loai bo records co gia <= 0 hoac category rong, Transform chuan hoa category va tinh gia khuyen mai 10%, cuoi cung Load ket qua ra file CSV. Bai cung thuc hien stress test de kiem tra anh huong cua du lieu xau den ket qua xu ly.

---

## Cach chay (How to Run)

### Prerequisites

Cai dat cac thu vien can thiet:

```bash
pip install pandas pytest
```

### Chay ETL Pipeline

```bash
python solution.py
```

Sau khi chay thanh cong, file `processed_data.csv` se duoc tao ra trong thu muc hien tai.

### Chay Tests

```bash
python -m pytest tests/test_autograder.py -v
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── raw_data.json            # Du lieu dau vao
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem stress test
└── README.md                # File nay
```

---

## Ket qua

Pipeline xu ly 5 records tu raw_data.json:
- 3 records hop le duoc giu lai va luu vao CSV
- 2 records bi loai (1 record co price <= 0, 1 record co category rong)
- Moi record duoc them cot discounted_price (giam 10%) va processed_at (timestamp)
