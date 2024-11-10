## Aplikasi Integrasi Direktorat SITP

# Contributing to Cosmonite

We would love for you to contribute to Cosmonite and help make it even better than it is today!
As a contributor, here are the guidelines we would like you to follow:

 - [Table](#table)
     1. [Basic Table](#basictable) 
     2. [Table With Custom Headers](#customheader) 
     3. [Table With Link](#tablelink) 



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


## <a name="tablelink"></a> Table With Link
if you wanna add link inside your table please modify ur body below 

please add type : linkhref

```shell
        column = 
        ...,{
            "label": "Admin",
            "value": "admin_count",
            "align": "center",
            "type": "linkhref"  # add this type
            } ,...
```

add this configuration on your JSON body 

 
```shell
        body: [{
            "kd_unit": "015.08",
            "kd_satker": "527010",
            "nm_satker": "KANTOR PUSAT DIREKTORAT JENDERAL PERBENDAHARAAN",
            "tipe": "SETPBN",
            "admin_count": [{routerLink: '../detailSummaryPenggunaSakti/527010/DITSMI/ROLE_ADMIN/PERAN',text: '3'}],
            "operator_count": 0,
            "validator_count": 0,
            "approver_count": 0,
            "aktif_count": [{routerLink: '../detailSummaryPenggunaSakti/527010/SETPBN/AKTIF/STATUS_DAFTAR',text: '7'}],
            "non_aktif_count": 0,
            "lainnya_count": 0
            }]
```

please use object of [ ] that contains two value routerLink and text. 

    1. The routerLink refers to the URL, i.e., your main URL:
        http://10.100.244.153:5000/omon/layout/data-view/admang/admin/summaryPenggunaAplikasi.
        - If you have a link that refers to a new function, such as summaryPenggunaAplikasiDetail, which is different from your main
        function, you need to use a relative path by adding ../ to your routerLink value to bypass the main route. It will look like this:
            ```diff
            routerLink="../summaryPenggunaAplikasiDetail/527010/UNIT/PERAN".
            ```
        
        - If your link is the same as your main function, then the routerLink should be:
        
            ```diff
            routerLink="/527010/UNIT/PERAN".
            ```

        - If your link is totally different, change the link from the base URL by adding this
            ```diff
            /layout/data-view/pelaporan/persediaset/persediaanUnapproved/"
            ```

    2. The text refers to the values of your rows.

🔴 notes : add toolbar for button back 

![Image](https://github.com/user-attachments/assets/be28aaef-b4f2-463e-aac5-2c96d3be9f23)

```shell
        toolbar : [
            {
                "label": "Kembali",
                "url": "/admservice/admin/summaryPenggunaAplikasi",
                "icon": "fa fa-arrow-left"
            }
        ]
```

monlap request 
![Image](https://github.com/user-attachments/assets/a7905d4d-73ea-413f-a318-44e18d7350a5)

🔴 notes: 
If the target link is a new tab, adjustments are needed in the body by adding the value target: '_blank'.
Then, the process of writing the routerLink needs to be adjusted; previously, it was only at the function name level and now needs to be adjusted up to the repository name.
```
body=[
                ...,
                "detail": [{routerLink: '../monlap/ledger/detailRekonAtas/3/630931/04',text: 'Detail',target: '_blank'}],
                ,...
         ]
```

if you wanna add some icon on your link this is the update for your json body 
```
body=[
               ...,"BAR": [{routerLink: '../monlap/ledger/BARekon/630931/04',text: 'Download',target: '_blank',class: 'fas fa-download'}],...
            ]
```

🟢Recomendations 
![Image](https://github.com/user-attachments/assets/db2025e6-beb1-4617-ad16-ea2e8d60f716)
 To look more beautiful, we suggest using column actions as shown in the image above. This can be done by making the following adjustments. Add 'actions' to your main JSON.

```shell
        {
            "subtitle": "Data Rekonsiliasi diperbarui setiap 6 jam, pembaruan terakhir pada: 24-10-2024 16:32<br>Penerbitan SHR diperbarui setiap jam, pembaruan terakhir pada: 24-10-2024 20:00",
            "title": "Rekonsiliasi SAKTI - SPAN Sampai Dengan Periode 2024-09",
            "column": [],
            "body": [],
            "split": 50,
            "filters": "",
            "toolbar": [],
            "actions": [                            # add this value
                {
                    "event": "detail",
                    "icon": "pi pi-sliders-h",
                    "class": "p-button-rounded p-button-info p-button-sm",
                    "label": "Lihat detail"
                },
                {
                    "event": "download",
                    "icon": "pi pi-download",
                    "class": "p-button-rounded p-button-warning p-button-sm",
                    "label": "Download"
                }
            ]
        }
```

add value actions only on your json body without define it on columns
```shell
    body:[
        {... ,"actions":[{detail:'../monlap/ledger/detailRekonAtas/3/630931/04',download:'../monlap/ledger/BARekon/630931/04'}],...}
            ]
```





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


