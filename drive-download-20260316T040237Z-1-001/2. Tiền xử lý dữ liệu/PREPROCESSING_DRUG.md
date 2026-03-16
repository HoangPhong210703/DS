# TỔNG HỢP TODO - PREPROCESSING DRUG

> **File notebook**: `preprocessing_drug_full.ipynb` > **Số lượng TODO**: 18 tasks
> **Thời gian ước tính**: 25-30 phút

---

## BẢNG TỔNG HỢP TODO

| #      | Vị trí     | Nội dung                         | Code mẫu                                                             | Độ khó |
| ------ | ---------- | -------------------------------- | -------------------------------------------------------------------- | ------ |
| **1**  | Line ~1430 | Chọn 5 cột features              | `X = my_data[['Age', 'Sex', 'BP', 'Cholesterol', 'Na_to_K']].values` | 1      |
| **2**  | Line ~1596 | Tạo LabelEncoder cho Sex         | `le_sex = preprocessing.LabelEncoder()`                              | 1      |
| **3**  | Line ~1597 | Fit encoder với Sex              | `le_sex.fit(['F', 'M'])`                                             | 1      |
| **4**  | Line ~1598 | Transform cột Sex                | `X[:, 1] = le_sex.transform(X[:, 1])`                                | 1      |
| **5**  | Line ~1609 | Tạo LabelEncoder cho BP          | `le_BP = preprocessing.LabelEncoder()`                               | 1      |
| **6**  | Line ~1610 | Fit encoder với BP               | `le_BP.fit(['HIGH', 'LOW', 'NORMAL'])`                               | 1      |
| **7**  | Line ~1611 | Transform cột BP                 | `X[:, 2] = le_BP.transform(X[:, 2])`                                 | 1      |
| **8**  | Line ~1622 | Tạo LabelEncoder cho Cholesterol | `le_Chol = preprocessing.LabelEncoder()`                             | 1      |
| **9**  | Line ~1623 | Fit encoder với Cholesterol      | `le_Chol.fit(['HIGH', 'NORMAL'])`                                    | 1      |
| **10** | Line ~1624 | Transform cột Cholesterol        | `X[:, 3] = le_Chol.transform(X[:, 3])`                               | 1      |
| **11** | Line ~1794 | Tính mean của Na_to_K            | `mean = X[:, -1].mean()`                                             | 2      |
| **12** | Line ~1795 | Tính std của Na_to_K             | `std = X[:, -1].std()`                                               | 2      |
| **13** | Line ~1802 | Áp dụng công thức z-score        | `X[:, -1] = (X[:, -1] - mean) / std`                                 | 3      |
| **14** | Line ~1969 | Chọn cột Drug làm target         | `y = my_data["Drug"]`                                                | 1      |
| **15** | Line ~2062 | Tạo LabelEncoder cho Drug        | `le_drug = preprocessing.LabelEncoder()`                             | 1      |
| **16** | Line ~2063 | Fit encoder với 5 loại thuốc     | `le_drug.fit(['drugA','drugB', 'drugC', 'drugX', 'drugY'])`          | 1      |
| **17** | Line ~2064 | Transform vector y               | `y_encoded = le_drug.transform(y)`                                   | 1      |
| **18** | Line ~2065 | Cập nhật y                       | `y = y_encoded`                                                      | 1      |

---

## QUY TRÌNH TIỀN XỬ LÝ (SIMPLIFIED)

```
[1] IMPORT LIBRARIES
     ↓
[2] UPLOAD & READ CSV
     ↓
[3] EXPLORE DATA
     ↓
[4] SPLIT X, y ← TODO #1
     ↓
[5] ENCODE FEATURES
     • Sex        ← TODO #2-4
     • BP         ← TODO #5-7
     • Cholesterol← TODO #8-10
     ↓
[6] STANDARDIZE
     • Na_to_K   ← TODO #11-13
     ↓
[7] SELECT TARGET ← TODO #14
     ↓
[8] ENCODE TARGET ← TODO #15-18
     ↓
[9] ML-READY!
```

---

## CHECKLIST HOÀN THÀNH

### Phần A: Tách dữ liệu (TODO #1)

- [ ] TODO #1: Tạo ma trận X với 5 cột features
- [ ] Kiểm tra: `X.shape == (200, 5)`

### Phần B: Encode Sex (TODO #2-4)

- [ ] TODO #2: Tạo `le_sex`
- [ ] TODO #3: Fit với `['F', 'M']`
- [ ] TODO #4: Transform cột 1
- [ ] Kiểm tra: `set(X[:, 1]) == {0, 1}`

### Phần C: Encode BP (TODO #5-7)

- [ ] TODO #5: Tạo `le_BP`
- [ ] TODO #6: Fit với `['HIGH', 'LOW', 'NORMAL']`
- [ ] TODO #7: Transform cột 2
- [ ] Kiểm tra: `set(X[:, 2]) == {0, 1, 2}`

### Phần D: Encode Cholesterol (TODO #8-10)

- [ ] TODO #8: Tạo `le_Chol`
- [ ] TODO #9: Fit với `['HIGH', 'NORMAL']`
- [ ] TODO #10: Transform cột 3
- [ ] Kiểm tra: `set(X[:, 3]) == {0, 1}`

### Phần E: Standardize Na_to_K (TODO #11-13)

- [ ] TODO #11: Tính `mean = X[:, -1].mean()`
- [ ] TODO #12: Tính `std = X[:, -1].std()`
- [ ] TODO #13: Áp dụng `z = (x - μ) / σ`
- [ ] Kiểm tra: `abs(X[:, -1].mean()) < 0.0001`
- [ ] Kiểm tra: `abs(X[:, -1].std() - 1) < 0.0001`

### Phần F: Tạo target (TODO #14)

- [ ] TODO #14: Tạo `y = my_data["Drug"]`
- [ ] Kiểm tra: `y.shape == (200,)`

### Phần G: Encode target (TODO #15-18)

- [ ] TODO #15: Tạo `le_drug`
- [ ] TODO #16: Fit với 5 loại thuốc
- [ ] TODO #17: Transform `y`
- [ ] TODO #18: Cập nhật `y = y_encoded`
- [ ] Kiểm tra: `set(y) == {0, 1, 2, 3, 4}`

---

## LƯU Ý QUAN TRỌNG

### 1. Thứ tự thực hiện

**Phải làm theo đúng thứ tự**: Encode trước → Standardize sau

### 2. Indexing NumPy array

```python
X[:, 0]   # Cột 0 (Age)
X[:, 1]   # Cột 1 (Sex)
X[:, 2]   # Cột 2 (BP)
X[:, 3]   # Cột 3 (Cholesterol)
X[:, -1]  # Cột cuối (Na_to_K)
```

### 3. LabelEncoder workflow

```python
le = LabelEncoder()         # Bước 1: Tạo encoder
le.fit(['A', 'B', 'C'])    # Bước 2: Học categories
le.transform(data)          # Bước 3: Chuyển đổi
```

### 4. Công thức Standardization

```python
z = (x - μ) / σ

μ (mu)    = mean (trung bình)
σ (sigma) = std (độ lệch chuẩn)
z         = z-score (giá trị chuẩn hóa)
```

---

## KẾT QUẢ CUỐI CÙNG

### Ma trận X (Features)

```python
X.shape: (200, 5)
X.dtype: float64

Cột 0: Age (15-74) - Giữ nguyên
Cột 1: Sex (0, 1) - Đã encode
Cột 2: BP (0, 1, 2) - Đã encode
Cột 3: Cholesterol (0, 1) - Đã encode
Cột 4: Na_to_K (mean≈0, std≈1) - Đã standardize
```

### Vector y (Target)

```python
y.shape: (200,)
y.dtype: int64

Giá trị: 0, 1, 2, 3, 4
(drugA, drugB, drugC, drugX, drugY)
```

---

## KIỂM TRA NHANH

### Script validation 1-line

```python
# Copy-paste để kiểm tra nhanh
assert X.shape == (200, 5) and y.shape == (200,) and set(X[:, 1]) == {0, 1} and set(X[:, 2]) == {0, 1, 2} and set(X[:, 3]) == {0, 1} and abs(X[:, -1].mean()) < 0.0001 and abs(X[:, -1].std() - 1) < 0.0001 and set(y) == {0, 1, 2, 3, 4}, "CÓ LỖI!"; print(" TẤT CẢ ĐÚNG!")
```

### Kiểm tra chi tiết

```python
print("=== KIỂM TRA KẾT QUẢ ===")
print(f"X.shape: {X.shape} {'OK' if X.shape == (200, 5) else 'FAIL'}")
print(f"y.shape: {y.shape} {'OK' if y.shape == (200,) else 'FAIL'}")
print(f"Sex encoded: {set(X[:, 1])} {'OK' if set(X[:, 1]) == {0, 1} else 'FAIL'}")
print(f"BP encoded: {set(X[:, 2])} {'OK' if set(X[:, 2]) == {0, 1, 2} else 'FAIL'}")
print(f"Chol encoded: {set(X[:, 3])} {'OK' if set(X[:, 3]) == {0, 1} else 'FAIL'}")
print(f"Na_to_K mean: {X[:, -1].mean():.6f} {'OK' if abs(X[:, -1].mean()) < 0.0001 else 'FAIL'}")
print(f"Na_to_K std: {X[:, -1].std():.6f} {'OK' if abs(X[:, -1].std() - 1) < 0.0001 else 'FAIL'}")
print(f"Target encoded: {set(y)} {'OK' if set(y) == {0, 1, 2, 3, 4} else 'FAIL'}")
```

---
