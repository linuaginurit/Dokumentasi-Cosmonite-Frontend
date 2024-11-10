## Aplikasi Integrasi Direktorat SITP

# Contributing to Cosmonite

We would love for you to contribute to Cosmonite and help make it even better than it is today!
As a contributor, here are the guidelines we would like you to follow:

 - [Table](#table)
     1. [Basic Table](#basictable) 
     2. [Table With Custom Headers](#customheader) 



## <a name="table"></a> Table

## <a name="basictable"></a> Basic Table
![Image](https://github.com/user-attachments/assets/6d4895e9-bcd4-49b1-ae2e-fc40d32fb0c0)

When you're trying to create basic table with omon please follow this format json bellow
```shell
            {
            "status": "success",
            "data": {
                "type": "table",
                "title": "Bagian Anggaran / Kewenangan / Sumber Dana / Wilayah",
                "subtitle": "Referensi Bagian Anggaran",
                "disclaimer": "",
                "columns": [
                    {
                        "value": "KODE",
                        "label": "Kode Angka",
                        "align": "left"
                    },
                    {
                        "value": "DESKRIPSI",
                        "label": "Kode Huruf",
                        "align": "left"
                    },
                    {
                        "value": "THANG",
                        "label": "Tahun Anggaran",
                        "align": "left"
                    },
                    {
                        "value": "TINGKAT",
                        "label": "Tingkat",
                        "align": "left"
                    }
                ],
                "toolbar": "",
                "filters": "",
                "body": [
                    {
                        "KODE": "001-2024",
                        "DESKRIPSI": "MAJELIS PERMUSYAWARATAN RAKYAT (MPR)",
                        "THANG": "2024",
                        "TINGKAT": "KL"
                    },
                    {
                        "KODE": "001.01-2024",
                        "DESKRIPSI": "Deputi Bidang Administrasi",
                        "THANG": "2024",
                        "TINGKAT": "Eselon 1"
                    }
                ],
                "split": 50,
                "disableSearch": false,
                "currentPage": 0,
                "totalRows": ""
            }
        }
```

## <a name="customheader"></a> Table With Custom Headers
![Image](https://github.com/user-attachments/assets/fead6931-52ec-4f16-b284-53dc5ede6f6a)

Creating row spans and column spans involves customizing the header of the table.
```shell
     ...,
            headers:[
                [
                    {
                        "label": [
                            "Kode Unit"
                        ],
                        "rowspan": 2,
                        "value": "kd_unit"
                    },
                    {
                        "label": [
                            "Kode"
                        ],
                        "rowspan": 2,
                        "value": "kd_satker"
                    },
                    {
                        "label": [
                            "Nama Satker"
                        ],
                        "rowspan": 2,
                        "value": "nm_satker"
                    },
                    {
                        "label": [
                            "Tipe"
                        ],
                        "rowspan": 2,
                        "value": "tipe"
                    },
                    {
                        "label": [
                            "Peran"
                        ],
                        "colspan": 4
                    },
                    {
                        "label": [
                            "Status Daftar"
                        ],
                        "colspan": 3
                    }
                ],
                [
                    {
                        "colspan": 1,
                        "label": [
                            "Admin"
                        ],
                        "value": "admin_count"
                    },
                    {
                        "colspan": 1,
                        "label": [
                            "Operator"
                        ],
                        "value": "operator_count"
                    },
                    {
                        "colspan": 1,
                        "label": [
                            "Validator"
                        ],
                        "value": "validator_count"
                    },
                    {
                        "colspan": 1,
                        "label": [
                            "Approver"
                        ],
                        "value": "approver_count"
                    },
                    {
                        "colspan": 1,
                        "label": [
                            "Aktif"
                        ],
                        "value": "aktif_count"
                    },
                    {
                        "colspan": 1,
                        "label": [
                            "Non Aktif"
                        ],
                        "value": "non_aktif_count"
                    },
                    {
                        "colspan": 1,
                        "label": [
                            "Lainnya"
                        ],
                        "value": "lainnya_count"
                    }
                ]
            ]
        ,...
```
        🟢 columns dan body tetap tidak ada perubahan
        🟢 Rowspan = menggabungkan baris
        🟢 colspan = menggabungkan kolom



# Perubahan Code
Perubahan Code yang bersifat global, hanya dilakukan sesuai dengan desain dari tim perancangan dan terdokumentasi pada Github Project. Jika tidak, maka akan di-revert 

# Konfigurasi Routing 
Pengguna dapat mengakses URL frontend berikut:

http://localhost:57447/layout/data-view/#repo/#nama-modul#/#feature#/#path

':repo/:ctrl_name/:function_name'

URL ini akan digunakan untuk membuat route ke backend dengan service berikut: 

   public getApiService(data): Observable<any> {
    const url = `${this.URL_ROOT_MONS}${data.repo}/${data.ctrl_name}/${data.function_name}/${paths.join('/')}`;
    return this.http.get<any>(url).pipe(
        catchError(this.handleError)
    );
}
  
Prasyarat

Pastikan bahwa bagian #repo/#nama-modul#/#feature# di URL frontend sama dengan alamat yang diakses di backend.

Frontend path: http://localhost:57447/layout/data-view/admang/nama-modul/feature

Backend path admang : http://localhost:8000/:repo/:ctrl_name/:function_name

Contoh

Jika Anda ingin mengakses backend menggunakan URL berikut:

#admang/anggaran/viewDataAng

Maka URL yang harus diakses adalah: 

http://localhost:57447/layout/data-view/admang/anggaran/viewDataAng

```diff
- nama-repo : admang
- nama-modul : anggaran
+ feature    : viewRefBanggar
```


