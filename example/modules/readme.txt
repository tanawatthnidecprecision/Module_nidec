/*
ใช้สำหรับดึงข้อมูล
สามารถโยนพารามิเตอร์ได้ 2 ตัว หรือจะไม่โยนก็ได้
ตัวแรกคือคำสั่ง sql สำหรับ where
ตัวที่สองคือ ชื่อตาราง
*/
const response = await $api.user_config.getConfig("index is not null");

const responseOther = await $api.user_config.getConfig(
  "index is not null",
  "daily_data"
);

/*
ใช้สำหรับส่งข้อมูล
ต้องโยนพารามิเตอร์ได้ 2 ตัว
ตัวแรกคือ object ของข้อมูล
ตัวที่สองคือชื่อตาราง หากไม่โยนจะมีค่าตั้งต้นเป็น user_config
*/
const responseInsert = await $api.user_config.postConfig(
  {
    index: 1199,
  },
  "aclivity_list"
);

/*
ใช้สำหรับอัปเดตข้อมูล
ต้องโยนพารามิเตอร์ได้ 3 ตัว
ตัวแรกคือ object ของข้อมูล
ตัวที่สองคือ คำสั่ง sql สำหรับ where
ตัวที่สามคือชื่อตาราง หากไม่โยนจะมีค่าตั้งต้นเป็น user_config
*/
const responseUpdate = await $api.user_config.updateConfig(
  {
    job: "kao",
  },
  "index = 1199",
  "aclivity_list"
);


/**/
$api.approve.create({
                    user_index: 7150,
                    type_index: 9999,
                    department_index: 0,
                    slip_index: 0,
                    approve_json: {
                      checked: checked.value,
                      acknowledge: acknowledge.value,
                    },
                  })

$api.approve.getState(
  approve_process_id
)

$api.approve.updateState(
  ลำดับ,
  `approve_process_id=${รหัส approve_process_id}`                  
)

$api.approve.postApproveAlarm({
                    user_index: 0,
                    slip_index: 0,
                    section_name: '',
                    type_index: 0,
                  })

/**/
$api.data_info.getInfoData()
$api.data_info.getDepartmentData()
$api.data_info.getLikeName("TA");



/**/
$api.paperless.post()
$api.paperless.getValue()
$api.paperless.update()



/*
สำหรับส่ง E-mail 
*/

/*
สำหรับ ค้นหาอีเมลด้วย ชื่อ นามสกุล
*/
$api.mail.getMail(ชื่อ, นามสกุล);
/*
สำหรับ ส่งอีเมล
*/
$api.mail.send(หัวข้อ,ข้อความ,อีเมล);