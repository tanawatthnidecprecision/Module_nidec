### Init
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

```
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
```
$api.approve.getState(
  approve_process_id
)
```

สำหรับอัปเดต สถานะของ approve_process 
```
$api.approve.updateState(
  ลำดับ,
  `approve_process_id=${รหัส approve_process_id}`                  
)
```

สำหรับสร้าง approve alarm 
```
$api.approve.postApproveAlarm({
                    user_index: 0,
                    slip_index: 0,
                    section_name: '',
                    type_index: 0,
                  })
```
## Data Info Service (สำหรับดึงข้อมูลส่วนบุคคล)
ใช้สำหรับดึงข้อมูลส่วนบุคคล (บล็อคการเข้าถึง password)
```
$api.data_info.getInfoData(user_index)
```

ใช้สำหรับดึงข้อมูลแผนก
```
$api.data_info.getDepartmentData(department_index)
```

ใช้สำหรับ ค้นหาชื่อเต็มใช้ใน 
```
$api.data_info.getLikeName("TA");
```

```
$api.paperless.post()
$api.paperless.getValue()
$api.paperless.update()
```



## Mail Service (สำหรับส่ง E-mail)

สำหรับ ค้นหาอีเมลด้วย ชื่อ นามสกุล
```
$api.mail.getMail(ชื่อ, นามสกุล);
```

สำหรับ ส่งอีเมล
```
$api.mail.send(หัวข้อ,ข้อความ,อีเมล);
```
