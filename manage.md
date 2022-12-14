# Basic Lightning Node

## การเปิดช่องกับ

คุณสามารถเปิดช่องกับผู้เข้าร่วมเครือข่ายใดก็ได้ที่คุณต้องการ อย่างไรก็ตาม มีหลายสิ่งที่ต้องพิจารณาก่อนที่จะทำเช่นนั้น

- เป็นคนที่คุณน่าจะทำธุรกรรมด้วยบ่อยๆ หรือไม่? หากเป็นเช่นนั้น ก็สมเหตุสมผลที่จะเปิดช่องทางโดยตรงเพื่อลดค่าธรรมเนียมการกำหนดเส้นทาง
- พวกเขาเป็นเพื่อนที่เชื่อถือได้หรือไม่? หากพวกเขาออฟไลน์เป็นประจำ สิ่งนี้จะทำให้คุณมีปัญหาเมื่อส่งหรือรับธุรกรรม
- พวกเขาเชื่อมต่อกันดีหรือไม่? หากคุณมีเพียร์เพียง 1 หรือ 2 คน การเชื่อมต่อที่ค่อนข้างดีจะช่วยให้พวกเขากำหนดเส้นทางธุรกรรมผ่านพวกเขาผ่านเครือข่ายได้ สิ่งนี้จะชัดเจนขึ้นในส่วนถัดไปเกี่ยวกับธุรกรรม
- พวกเขาเชื่อถือได้หรือไม่? ซึ่งครอบคลุมรายละเอียดด้านล่าง แต่เพื่อนของคุณมีตัวเลือก (แม้ว่าจะไม่น่าจะทำสำเร็จ) ที่จะพยายามโกงคุณเมื่อปิดช่อง ช่วยให้คุณไม่ต้องยุ่งยากในการเลือกเพื่อนที่คุณรู้จักหรือเอนทิตีโหนดสาธารณะที่ยอมรับกันโดยทั่วไปว่าเป็นผู้ดำเนินการโหนดที่ซื่อสัตย์

คุณสามารถเปรียบเทียบสถิติเหล่านี้และอื่นๆ อีกมากมายเมื่อเลือกเพียร์ที่ [1ml](https://1ml.com/) หรือใช้เวอร์ชันที่เรียบง่าย[ที่นี่](https://nodes.lightning.computer/availability/v1/btc.json) ซึ่งจะให้คะแนนรวมของโหนดโดยพิจารณาจากการรวมกันของสิ่งต่างๆ เช่น เวลาทำงาน สภาพคล่อง และการเชื่อมต่อที่ดี จากนั้นจะแสดง 5% ที่ดีที่สุด

## การปิดช่อง

เช่นเดียวกับการเปิดช่อง การปิดช่องเป็นธุรกรรม Bitcoin on-chain การปิดช่องเกิดขึ้นเมื่อ **ฝ่ายใดฝ่ายหนึ่ง หรือ ทั้งสองฝ่าย ต้องการชำระยอดคงเหลือกลับไปยังเครือข่าย Bitcoin** มีการปิดช่องสามประเภทที่อาจเกิดขึ้นกับ Lightning และ ในทุกกรณี ค่าธรรมเนียมจะจ่ายโดยบุคคลที่เปิดช่อง

**Collaborative close**

เมื่อฝ่ายใดฝ่ายหนึ่งเริ่มปิดช่อง ให้แจ้งเรื่องนี้กับพันธมิตรช่องของตน ทั้งสองฝ่ายตกลงที่จะปิดช่อง และ สถานะล่าสุด จะถูกส่งไปยังเครือข่ายและผู้เข้าร่วมแต่ละคนจะได้รับ sats ของพวกเขากลับไปที่กระเป๋าเงินโซ่ สถานการณ์นี้ครอบคลุมส่วนใหญ่ของการปิดช่อง Lightning ทั้งหมด

**Force Close**

เมื่อฝ่ายใดฝ่ายหนึ่งปิดช่องทางโดยไม่ได้รับความยินยอมจากคู่สัญญา การปิดประเภทนี้ **มักเกิดขึ้นเมื่อฝ่ายใดฝ่ายหนึ่งไม่สามารถติดต่อได้** สำหรับการบังคับที่ใกล้จะเกิดขึ้น ผู้ใช้คนหนึ่งเพียงประกาศสถานะช่องล่าสุดที่พวกเขารู้จัก เมื่อการบังคับปิดได้รับการ**ยืนยัน**บนบล็อกเชน ผู้ใช้ที่เริ่มการบังคับปิดจะถูกล็อคยอดคงเหลือตามระยะเวลาที่กำหนด ซึ่งช่วยให้คู่สัญญาของพวกเขาเห็นช่องปิด และกลับมาออนไลน์ เพื่อยืนยันสถานะช่อง หากไม่เกิดขึ้น ฝ่ายที่ปิดช่องทางของกองทุนลูกโซ่ จะสามารถ**ใช้จ่ายได้หลังจากเวลาล็อคสิ้นสุดลง**

**Disputed close**

การปิดที่มีข้อพิพาทเกิดขึ้นจากการบังคับปิดที่เริ่มต้นขึ้น หากฝ่ายที่ริเริ่มเผยแพร่สถานะช่องเก่าที่สนับสนุนพวกเขาและจ่ายเงินคืนให้กับพวกเขามากขึ้น บุคคลที่ปิดช่องสามารถโต้แย้งการปิดได้หากพวกเขาไม่เห็นด้วยกับผลลัพธ์ หากต้องการจุดชนวนข้อพิพาทนี้ พวกเขาเพียงแค่นำโหนดของตนกลับมาออนไลน์ภายในช่วงล็อกเอาต์ อีกทางหนึ่ง หากนั่นไม่ใช่ตัวเลือกเนื่องจากโหนดของพวกเขาอยู่ในตำแหน่งทางภูมิศาสตร์ที่แตกต่างกัน พวกเขาอาจเลือกที่จะตั้งค่า บริการ [Watchtower](https://bitcoinmagazine.com/technical/watchtowers-are-coming-lightning) ที่จะตรวจสอบช่องของพวกเขาและดำเนินการในนามของพวกเขาโดยมีค่าธรรมเนียมเล็กน้อย

หากฝ่ายที่สร้างข้อพิพาทสามารถเผยแพร่สถานะช่องล่าสุดได้สำเร็จมากกว่าสถานะช่องที่ออกอากาศโดยพันธมิตรช่องของพวกเขา โหนดของพวกเขาจะสามารถเผยแพร่ [Justice transaction](https://bitcoinmagazine.com/technical/bitmex-research-confirms-lightning-justice-works) และเรียกร้องยอดคงเหลือทั้งหมดของช่องได้ ภัยคุกคามของสถานการณ์ดังกล่าวก็เพียงพอแล้วที่จะปัดเป่าผู้ให้บริการ Lightning ที่ไม่ซื่อสัตย์ส่วนใหญ่เพราะกลัวว่าจะสูญเสียเงินทุนทั้งหมด

## คำถามที่พบบ่อย

**ฉันจำเป็นต้องใช้สายฟ้าหรือไม่?**

ไม่มีคำตอบที่ถูกหรือผิดที่นี่ ในปัจจุบัน ค่าธรรมเนียม Bitcoin ยังคงค่อนข้างถูก ซึ่งทำให้การทำธุรกรรมแบบ on chain transactions เป็นที่ยอมรับสำหรับผู้ใช้ 95% แต่สำหรับผู้ที่ทำธุรกรรมเป็นประจำโดยใช้จำนวนเงินที่น้อยลง Lightning นำเสนอโอกาสในการประหยัดค่าธรรมเนียม และ ยังได้รับประโยชน์จากการชำระธุรกรรมที่เกือบจะทันที

**ฉันต้องการโหนดหรือไม่?**

เช่นเดียวกับ Bitcoin คุณไม่จำเป็นต้องมีโหนดเพื่อโต้ตอบกับ Lightning แต่การเรียกใช้โหนดของคุณเองเป็นวิธีที่**เป็นส่วนตัว**และ**ปลอดภัยที่สุด** ถ้าคุณไม่ไว้ใจตัวเอง แสดงว่าคุณกำลังไว้ใจคนอื่น โชคดีที่โหนด Bitcoin ทั่วไปส่วนใหญ่มาพร้อมกับการใช้งาน Lightning ด้วย 

**ใครเป็นผู้ดูแลเครือข่าย Lightning?**

เครือข่าย Lightning เป็นโปรโตคอลแบบเปิดที่หลายคนทำงาน และ มีส่วนร่วม การใช้งานทั้งหมดทำงานตามมาตรฐานเปิดของ [BOLT](https://github.com/lightning/bolts/blob/master/00-introduction.md) และ การใช้งานทั่วไปสามารถทำงานร่วมกันได้อย่างสมบูรณ์
- [LND](https://github.com/lightningnetwork/lnd)
- [C Lightning](https://github.com/ElementsProject/lightning)
- [Eclair](https://github.com/ACINQ/eclair)

**มี 'Lightning coin' หรือไม่?**

ไม่ ธุรกรรม Lightning เป็นการโอนความเป็นเจ้าของ bitcoin จากบุคคลหนึ่งไปยังอีกบุคคลหนึ่งเป็นหลัก

**เหตุใดการชำระเงินจึงล้มเหลว?**

ความล้มเหลวในการชำระเงินเกิดขึ้นได้จากหลายสาเหตุ อย่างไรก็ตาม สาเหตุที่พบบ่อยที่สุดคือโหนดที่คุณกำลังทำธุรกรรมไม่พบเส้นทางการชำระเงินที่เหมาะสมไปยังปลายทาง

**ช่องสัญญาณที่สมดุลหมายถึงอะไร?**

การมีช่องทางสมดุลนั้นหมายความว่าคุณมีจำนวน sats เท่ากัน ทั้งสองด้านของช่องของคุณ ให้คิดว่ามันเหมือน ลูกคิด ที่มี ลูกปัดเท่ากันในแต่ละด้าน สิ่งนี้ทำให้มั่นใจได้ว่าผู้ใช้อยู่ในตำแหน่งที่ดีที่สุดในการส่งหรือรับผ่าน Lightning นอกจากนี้ยังเป็นประโยชน์สำหรับผู้ที่ต้องการรับ sats ด้วยการเป็น routing node แม้ว่าแนวคิดดังกล่าวสำหรับผู้ใช้ขั้นสูง

**ฉันจะสร้างความสมดุลให้กับช่องของฉันได้อย่างไร?**

เครื่องมือจัดการโหนด Lightning ที่ใช้กันมากที่สุด 2 ตัวคือ [Ride the Lightning](https://twitter.com/Suheb__/status/1228470045715681280?s=20) และ [Thunderhub](https://apotdevin.com/blog/thunderhub-balancing) ทำให้สิ่งนี้ง่ายมากในอินเทอร์เฟซผู้ใช้ คลิกลิงก์เพื่อดูวิดีโอสาธิตของทั้งคู่

**จะเกิดอะไรขึ้นหากโหนดของฉันหยุดทำงานในขณะที่ฉันมีช่องเปิดอยู่?**

ทางออกที่ดีที่สุดคือการฟื้นฟูโหนดของคุณ และ หลีกเลี่ยงความจำเป็นในการปิดแชนเนลของคุณตั้งแต่แรก อย่างไรก็ตาม สิ่งนี้จะไม่สามารถทำได้เสมอไป และ นี่คือจุดที่การสำรองข้อมูลมีความสำคัญ คุณสามารถนำเข้า Lightning Wallet seed และ ไฟล์สำรองแชนเนลแบบสแตติกไปยัง Lightning Node อื่นได้ ซึ่งจะทริกเกอร์การแจ้งเตือนการปิดไปยังเพื่อนทั้งหมด และส่ง sats ของคุณกลับไปยังกระเป๋าเงินเครือข่ายของคุณ กระบวนการนี้สามารถทำได้ผ่านบรรทัดคำสั่ง แต่เป็นวิธีที่ง่ายที่สุดที่จะทำ ผ่านอินเทอร์เฟซเช่น RTL หรือ Thunderhub ผลลัพธ์อีกอย่างคือ Lightning peer อาจสังเกตว่าคุณออฟไลน์อยู่ และ เลือกที่จะบังคับปิดช่อง (หวังว่าจะพูดตรงๆ) ซึ่งจะเป็นการคืน sats ใดๆ ในช่องนั้นกลับไปที่กระเป๋าสตางค์เชนของคุณ

**เหตุใดยอดคงเหลือของช่องของฉันจึงเปลี่ยนแปลงเมื่อเวลาผ่านไป?**

อาจเป็นเพราะ **มีบางคนกำหนดเส้นทางธุรกรรมผ่านโหนดของคุณ** สิ่งนี้มีผลในการย้ายความสมดุลบางส่วนจากด้านหนึ่งของช่อง ไปยังอีกด้านหนึ่ง **หากคุณไม่ต้องการให้สิ่งนี้เกิดขึ้น คุณสามารถระบุได้ว่าช่องของคุณเป็นแบบส่วนตัว**ในขณะที่เปิด สิ่งนี้จะป้องกันไม่ให้มองเห็นได้อย่างมีประสิทธิภาพสำหรับเครือข่ายที่เหลือ

**ฉันจะโอน sats ของฉันออกจาก Lightning ได้อย่างไร?**

คุณสามารถปิดช่องได้ ซึ่งจะคืนยอดเงินของคุณกลับไปยังกระเป๋าเงินเครือข่ายของคุณ อีกทางเลือกหนึ่ง 

หากคุณได้รับการชำระเงินแบบ Lightning จำนวนมาก และ ยอดคงเหลือของช่องของคุณเริ่มเต็ม คุณสามารถดำเนินการ [วนซ้ำ (Loop)](https://lightning.engineering/loop/)ได้ซึ่งจะทำให้เปอร์เซ็นต์ของยอดคงเหลือในช่องทางของคุณไหลกลับไปยังกระเป๋าเงินเครือข่าย ทำให้ความจุของช่องว่างมากขึ้นเพื่อให้คุณได้รับ อีกครั้ง. การดำเนินการย้อนกลับ (วนซ้ำ) สามารถใช้เพื่อ 'เติม' ยอดคงเหลือในช่องทางของคุณ หากคุณชำระเงินจำนวนมากและไม่มีสภาพคล่องขาออกที่เพียงพออีกต่อไป

[CoinOS](https://coinos.io/) นำเสนอทางเลือกที่ดีอีกทางหนึ่งสำหรับการแลกเปลี่ยนระหว่างเชน และ ออฟเชนอย่างง่ายดาย อย่าลืมใช้ตัวเลือก non-custodial เพื่อลบล้างความเสี่ยงของบุคคลที่สาม

**ฉันจะทำให้ช่องของฉันใหญ่ขึ้นหลังจากเปิดแล้วได้ไหม?**

ไม่ ขนาดช่องจะคงที่เมื่อเปิด อย่างไรก็ตาม คุณสามารถใช้ประโยชน์จากหลายช่องทางพร้อมกันได้โดยใช้การชำระเงินแบบหลายเส้นทาง

**ฉันสามารถหารายได้บน Lightning Network ได้หรือไม่?**

ใช่ ในทางเทคนิคแล้ว คุณสามารถได้รับ sats ผ่านการกำหนดเส้นทาง อย่างไรก็ตาม ข้อดีที่จะได้รับเมื่อเทียบกับโหนด และ การจัดการแชนเนลที่จำเป็น ทำให้การปฏิบัตินี้อยู่นอกเหนือการเข้าถึงสำหรับผู้ใช้ Lightning ทั่วไป

**มีค่าใช้จ่ายเท่าไรในการเปิดหรือปิดช่อง?**

ขึ้นอยู่กับสถานะปัจจุบันของ Bitcoin mempool ในขณะนั้น และ อัตราค่าธรรมเนียมที่เจรจากับพันธมิตรช่องทางของคุณ

**Keysend คืออะไร?**

Keysend คือการพัฒนาที่ช่วยให้สามารถกำหนดเส้นทางการชำระเงินโดยไม่ต้องใช้ใบแจ้งหนี้

**MPP คืออะไร?**

การชำระเงินแบบหลายเส้นทาง ([Multi Path Payments](https://lightning.engineering/posts/2020-05-07-mpp/))ช่วยให้ผู้ใช้สามารถส่งการชำระเงินที่มากกว่าความจุของช่องทางที่ใหญ่ที่สุดเพียงช่องทางเดียวได้ โดยใช้สภาพคล่องของช่องทางมากกว่า 1 ช่องทาง ในเวลาเดียวกัน สิ่งนี้จำเป็นต้องเปิดใช้งานที่ระดับโหนด
