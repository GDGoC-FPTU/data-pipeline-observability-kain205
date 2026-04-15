# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600138
**Name:** Nguyen Binh Thanh
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay ETL pipeline voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Records Dau Vao | Records Hop Le | Records Bi Drop | Accuracy (1-10) | Notes |
|----------|----------------|----------------|-----------------|-----------------|-------|
| Clean Data (`raw_data.json`) | 5 | 3 | 2 | 9 | Pipeline chay on dinh, ket qua chinh xac |
| Garbage Data (du lieu xau) | 5 | 0-1 | 4-5 | 2 | Rat nhieu records bi drop, ket qua khong dang tin |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung du lieu xau (garbage data), pipeline gap nhieu van de nghiem trong anh huong den chat luong ket qua dau ra. Cu the, cac van de bao gom: gia tri price am hoac bang 0 khong co nghia thuc te, category bi de trong khong the phan loai san pham, va cac outlier bat thuong lam sai lech cac phep tinh thong ke nhu gia trung binh hay tong doanh thu.

Du lieu xau cung gay ra hieu ung domino: khi validate() loai bo qua nhieu records, DataFrame dau ra co rat it ban ghi, dan den ket qua phan tich thieu do chinh xac va khong dai dien cho toan bo tap du lieu. Gia discounted_price tinh tren nen price sai se tao ra cac gia khuyen mai vo nghia. Ngoai ra, neu category khong duoc chuan hoa dung (Title Case), viec group-by va aggregate theo category se cho ket qua sai hoan toan voi nhieu nhom trung lap.

Ket luan: Garbage In, Garbage Out - chat luong du lieu dau vao quyet dinh truc tiep den do tin cay cua toan bo pipeline va cac phan tich phu thuoc vao no.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Du lieu chat luong cao quan trong hon la cau lenh (prompt) tot. Mot pipeline xu ly tot voi du lieu xau van cho ra ket qua sai. Nguoc lai, du lieu sach se giup bat ky thuat toan nao cung hoat dong hieu qua hon. Dau tu vao validation va lam sach du lieu la buoc quan trong nhat trong bat ky he thong xu ly du lieu nao.
