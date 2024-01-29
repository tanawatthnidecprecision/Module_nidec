![image](https://i.ibb.co/PtrwNmd/0f483c07-4683-4c97-ba7b-a0de3c12b34d-removebg-preview.png)

### Initialize
```JS
import { $api } from "https://tanawatthnidecprecision.github.io/Module_nidec/nidec.min.js";

window.addEventListener("load", async () => {
  console.log(await $api.user_config.getConfig("index is not null"));
});
```

### Persornal Service

ใช้สำหรับดึงข้อมูล
สามารถโยนพารามิเตอร์ได้ 2 ตัว หรือจะไม่โยนก็ได้
ตัวแรกคือคำสั่ง sql สำหรับ where
ตัวที่สองคือ ชื่อตาราง

```JS
const response = await $api.user_config.getConfig("index is not null");
```

```JS
const responseOther = await $api.user_config.getConfig(
  "index is not null",
  "daily_data"
);
```

ใช้สำหรับส่งข้อมูล
ต้องโยนพารามิเตอร์ได้ 2 ตัว
ตัวแรกคือ object ของข้อมูล
ตัวที่สองคือชื่อตาราง หากไม่โยนจะมีค่าตั้งต้นเป็น user_config
```JS
const responseInsert = await $api.user_config.postConfig(
  {
    index: 1199,
  },
  "aclivity_list"
);
```

ใช้สำหรับอัปเดตข้อมูล
ต้องโยนพารามิเตอร์ได้ 3 ตัว
ตัวแรกคือ object ของข้อมูล
ตัวที่สองคือ คำสั่ง sql สำหรับ where
ตัวที่สามคือชื่อตาราง หากไม่โยนจะมีค่าตั้งต้นเป็น user_config

```JS
const responseUpdate = await $api.user_config.updateConfig(
  {
    job: "kao",
  },
  "index = 1199",
  "aclivity_list"
);
```

## Approve Service

สำหรับสร้าง approve_process และ approve_process_flow 
```JS
$api.approve.create({
  user_index: 0,
  type_index: 0,
  department_index: 0,
  slip_index: 0,
  approve_json: { // ตัวอย่าง
    checked: checked.value,
    acknowledge: acknowledge.value,
  },
})
```

สำหรับสร้าง ดึงสถานะของ approve_process 
```JS
$api.approve.getState(
  approve_process_id
)
```

สำหรับอัปเดต สถานะของ approve_process 
```JS
$api.approve.updateState(
  ลำดับ,
  `approve_process_id=${รหัส approve_process_id}`                  
)
```

สำหรับสร้าง approve alarm 
```JS
$api.approve.postApproveAlarm({
  user_index: 0,
  slip_index: 0,
  section_name: '',
  type_index: 0
})
```
## Data Info Service (สำหรับดึงข้อมูลส่วนบุคคล)
ใช้สำหรับดึงข้อมูลส่วนบุคคล (บล็อคการเข้าถึง password)
```
$api.data_info.getInfoData(user_index)
```

ใช้สำหรับดึงข้อมูลแผนก
```JS
$api.data_info.getDepartmentData(department_index)
```

ใช้สำหรับ ค้นหาชื่อเต็มใช้ใน 
```JS
$api.data_info.getLikeName(ชื่อ);
```

ใช้สำหรับส่งข้อมูล paperless
##### *ข้อมูลที่จะนำเข้าชื่อ key ต้องตรงกับ colums ใน table
```JS
$api.paperless.post(JSON)
```

ใช้สำหรับดึงข้อมูล paperless ต้องกำหนดเงื่อนไข
```JS
$api.paperless.getValue(
  table_name,
  "approve_process_id",
  approve_process_id
)
```

ใช้สำหรับอัปเดตข้อมูล paperless ต้องกำหนดเงื่อนไข และชื่อของฐานข้อมูล
```JS
$api.paperless.update({
  condition: "approve_process_id=0",
  data: {
    comment: JSON.stringify(JSON),
  },
  table_name: "ชื่อ table_name",
})
```



## Mail Service (สำหรับส่ง E-mail)

สำหรับ ค้นหาอีเมลด้วย ชื่อ นามสกุล
```JS
$api.mail.getMail(ชื่อ, นามสกุล);
```

สำหรับ ส่งอีเมล
```JS
$api.mail.send(หัวข้อ,ข้อความ,อีเมล);
```


## IO Service (สำหรับทำงานเกี่ยวกับไฟล์)

สำหรับ อัปโหลดไฟล์ขึ้น Server
```JS
$api.io.uploadFile(file);
```

สำหรับ แสดงไฟลืที่อัปโหลดขึ้นไป
```JS
$api.io.getFile(ชื่อไฟล์);
```

## AGV Service (สำหรับใช้งานกับหุ่นยนต์ )
