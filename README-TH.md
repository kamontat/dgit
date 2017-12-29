# dgit(1) - ระบบที่จัดเก็บการเปลี่ยนแปลงสำหรับนักออกแบบ

- [ตั้งค่า](#setup)
- [การใช้งาน](#usage)
- [ตัวอย่าง](#example)
- [รูปแบบการใช้งาน](#app-flow)
- [รูปภาพ](#images)
- [อื่นๆ](#miscellaneous)
  - [การติดตั้งในวินโดวส์](#install-window)
  - [การติดตั้งในลินุกส์และแมค](#install-unix)
  - [การช่วยเหลืออัตโนมัติในซีเชล](#zsh-completions)
  - [กิต](#git)

## Setup

การตั้งค่าบางอย่างอาจจะต้องใช้ความชำนาญพอสมควร ดังนั้นควรให้นักพัฒนามาตั้งค่าให้ 
หากแต่ถ้าท่านต้องการตั้งค่าเอง ท่านสามาถลองทำตามวิธีข้างล่างนี้ได้เลย

1. ติดตั้งคำสั้ง `กิต` โดย [ลิงค์](https://git-scm.com/downloads) ([เพิ่มเติมเกี่ยวกับกิต](#git))
1. คำสั้งนี้ ต้องการ `bash (แบช)` เวอร์ชั่น 4 ขึ้นไป หรือ ใช้ `zsh (ซีเชล)` ก็ได้, ผมแนะนำให้ลงเวอร์ชั่นล่าสุดเลย
    1. วินโดวส์ - ต้องการ วินโดวส์ 10 ขึ้นไป**เท่านั้น** [วิธี](http://www.artit-k.com/how-to-enable-bash-on-ubuntu-on-windows-10-build-14316/)
    1. ลินุกส์ - bash (แบช) นั้นได้มีการลงมาเป็นพื้นฐานอยู่แล้ว ดังนั้นท่านแค่อัพเดตเป็นเวอร์ชั่นล่าสุดก็พอ (ท่านสามารถเช็คเวอร์ชั่นโดยคำสั้ง `bash --version`)
    1. แมค - อัพเดต bash (แบช) เวอร์ชั่นในแมค คุณจำเป็นต้องลง [homebrew](https://brew.sh) ก่อน หลังจากนั้นก็รันคำสั้ง `brew install bash`
1. หากคุณใช้ zsh (ซีเชล), คุณจะสามารถใช้งาน **การช่วยเหลืออัตโนมัติ** ได้ แต่ว่าการตั้งค่าของมันจะค่อนข้างยาก ดังนั้นถามหานักพัฒนาสักคนมาทำให้จะดีกว่า
    1. ในการตั้งค่า ให้ทำตาม [วิธีนี้](#zsh-completions)
1. เพื่อใช้งานได้อย่างสะดวกและง่าย คุณอาจจะต้องติดตั้งไฟล์ไว้ในเครื่อง *สิ่งนี้ไม่ได้เป็นสิ่งจำเป็น เพียงแต่จะช่วยให้การใช้งานสะดวกขึ้นเท่านั้น* ([วินโดวส์](install-window), [แมค](install-unix), [ลินุกส์](install-unix))

## Usage

1. หากคุณไม่ได้ติดตั้ง คุณจะเรียกใช้งานโดย `/xx/yy/ws การกระทำ [รูปแบบ] [อาร์กิวเมนต์]..`
1. หากคุณติดตั้งแล้ว คุณจะเรียกใช้งานโดย `ws การกระทำ [รูปแบบ] [อาร์กิวเมนต์]..`
1. หากคุณต้องการข้อมูลเพิ่มเติม คุณสามารถรันโดย `ws help` ได้

## Example

1. `ws list all` - โชว์ ทั้งหมด (ทั้ง state และ version)
1. `ws save version version-1 "finish dark mode"` - สร้างเวอร์ชั่นใหม่พร้อมข้อความอธิบาย
1. `ws checkout version-1-light` - ย้ายข้อมูลไปยัง เวอร์ชั่น **version-1-light**

## App flow

1. เริ่มต้นงาน - `ws init`
1. (ทำงาน)
    1. (ยังไม่เสร็จ) - บันทึกงานโดย `ws save state`
    1. (เสร็จแล้ว) - บันทึกเวอร์ชั่นโดย `ws save version v1-dark-theme`
1. (ทำบางอย่างผิด)
    1. (มีการบันทึกแล้ว) - ย้ายไปงานเก่าที่ได้บันทึกไว้ `ws checkout state c5d1c33`
    1. (ลืมบันทึก) - ทำใจ
1. (มีเวอร์ชั่นเยอะมาก)
    1. (เปรียบเทียบ) - ย้ายไปยังเวอร์ชั่นเก่าๆโดย `ws checkout version v1-hot-theme`
1. จบโปรเจก ไม่สามารถย้านกลับได้ - `ws teardown`
1. ลืมวิธีใช้ - `ws help`

## Images

<details>
    <summary>ตัวช่วย</summary>

![help](/images/help.png)

</details>

<details>
    <summary>ตัวอย่างการใช้งาน</summary>

<details>
    <summary>ตัวอย่างการโชว์ประวัติ</summary>

![l-all](/images/list-all.png)

![l-state](/images/list-state.png)

![l-version](/images/list-version.png)

</details>

<details>
    <summary>ตัวอย่างการบันทึกงาน</summary>

![s-state](/images/save-state.png)

![s-version](/images/save-version.png)

</details>

<details>
    <summary>ตัวอย่างการย้ายข้อมูล</summary>

![checkout](/images/checkout.png)

</details>

</details>

<details>
    <summary>การช่วยเหลืออัตโนมัติ</summary>

![ac-co1](/images/auto-completion-checkout-1.png)

![ac-co2](/images/auto-completion-checkout-2.png)

![ac](/images/auto-completion-main.png)

</details>

## Miscellaneous

### Install Window

ไม่ทราบ

### Install Unix

1. ย้ายไฟล์ `ws` ไปยัง `/usr/local/bin`
1. ทำให้ `ws` สามารถกำเนินการได้โดย `chmod +x /usr/local/bin/ws`

### ZSH Completions

1. ย้ายไฟล์ `_ws` ไปยัง `/usr/local/share/zsh/site-functions`

### Git

**git** คือระบบที่จัดเก็บการเปลี่ยนแปลงอย่างหนึ่งที่นักพัฒนาส่วนมากใช้กัน

1. [ข้อมูลเพิ่มเติม (ไทย)](https://git-scm.com/book/th/v1/เริ่มต้นใช้งาน-เกี่ยวกับ-Version-Control)
1. [ข้อมูลเพิ่มเติม (อังกฤษ)](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
