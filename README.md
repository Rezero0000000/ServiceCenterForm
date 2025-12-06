### Script
1. Pilih Ekstensi
2. Apps Script
3. Masukan Kode berikut

```
function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSheet();

  const header = [
    "CS Name",
    "Customer Name",
    "Date",
    "Address",
    "Phone",
    "WO Type",
    "Product",
    "Product Type",
    "Problem Reported",
    "Problem Found",
    "Problem Type",
    "Engineer Name",
    "Action Date",
    "Start Time",
    "Stop Time",
    "Action Taken",
    "Status",
    "Signature",
    "Timestamp"
  ];

  const lastRow = sheet.getLastRow();

  if (lastRow === 0) {
    sheet.appendRow(header); // buat header di baris 1
  } else {
    // cek apakah baris pertama kosong
    const firstRow = sheet.getRange(1, 1, 1, header.length).getValues()[0];
    const isHeaderEmpty = firstRow.every(v => v === "");
    
    if (isHeaderEmpty) {
      sheet.getRange(1, 1, 1, header.length).setValues([header]);
    }
  }

  sheet.appendRow([
    e.parameter.cs_name,
    e.parameter.customer_name,
    e.parameter.date,
    e.parameter.address,
    e.parameter.phone,
    e.parameter.wotype,
    e.parameter.product,
    e.parameter.product_type,
    e.parameter.problem_reported,
    e.parameter.problem_found,
    e.parameter.problem_type,
    e.parameter.engineer_name,
    e.parameter.action_date,
    e.parameter.start_time,
    e.parameter.stop_time,
    e.parameter.action_taken,
    e.parameter.status,
    e.parameter.signature,
    new Date()
  ]);

  return ContentService.createTextOutput("Success");
}
```

4. Save
5. Terapkan
6. Deployment Baru
7. Lanjutkan Sesuai Petunjuk