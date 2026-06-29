# Manual QA Testing Portfolio – Sauce Demo

Manual QA testing untuk fitur Authentication (Registration & Login) pada
[Sauce Demo](https://sauce-demo.myshopify.com), dilakukan tanpa PRD menggunakan
industry best practices sebagai referensi.

---

## Temuan Utama

### Functional Defects

**TC-REG-004** — Semua field di-clear setelah password validation error, termasuk
First Name, Last Name, dan Email yang valid. Expected: hanya password field yang
dikosongkan.

**TC-REG-007** — Inconsistency validasi antara First Name dan Last Name: First Name
menerima 255 karakter, Last Name menolaknya dengan pesan "maximum is 255 characters".
Batas aktual Last Name tidak terdokumentasi.

### UX Improvement Reports

**UX-001** — Registration form melakukan global form reset saat validasi gagal,
membuang 75% data yang sudah diisi user. Rekomendasi: retain semua non-sensitive
field, clear hanya password.

**UX-002** — Login form mengosongkan email field setelah failed attempt, berbeda
dari standar industri (Gmail, Amazon, Facebook). Rekomendasi: retain email, clear
password saja.

### Observasi Teknis

TC-LOG-006 dan TC-LOG-007 menunjukkan browser-level validation (HTML5) yang memblock
submission sebelum request dikirim ke server, sehingga field tidak di-clear. TC-LOG-008
menunjukkan server-side validation dengan perilaku berbeda — field di-clear setelah
response diterima. Inconsistency ini didokumentasikan sebagai UX issue.

---

## Cakupan Testing

| Modul | Jumlah TC | Pass | Fail |
|---|---|---|---|
| Registration | 10 | 8 | 2 |
| Login | 8 | 7 | 1 |
| **Total** | **18** | **15** | **3** |

Tipe skenario: positive, negative, boundary, validation — tanpa PRD.

---

## Struktur Repository

```
├── test-case/
│   ├── TC_Registration.md     # 10 test cases
│   └── TC_Login.md            # 8 test cases
├── ux-reports/
│   ├── UX-001_Registration_Data_Retention.md
│   └── UX-002_Login_Data_Retention.md
└── test-summary/
    └── Login_test_summary.md
```

---

## Pendekatan Testing

- Black-box testing tanpa akses source code
- Pemisahan eksplisit antara functional defect dan UX observation
- Dokumentasi perbedaan behavior antara browser-level dan server-side validation

**Environment:** Chrome · Windows 11 · Sauce Demo (Shopify-based)
