# Language-Translation
## Language Translation using IBM Watson

### Python จะใช้ในการจับข้อความ หลังจากนั้นจะถูกส่งไปยัง IBM cloud เพื่อแปลเป็นภาษาที่เลือก จากนั้น Watson AI จะถูกใช้เพื่อเปลี่ยนข้อความที่แปลเป็นคำพูด จากนั้นไฟล์จะถูกส่งออกไป


### Workflow

**เราจะบันทึกข้อความใน `python` จากนั้นเราจะส่งข้อมูลนี้ไปยังคลาวด์ `IBM` ซึ่งข้อความจะถูกแปลงเป็นภาษาที่เราต้องการ และเราจะแปลง `ข้อความที่แปลแล้ว' เป็นคำพูด โดยใช้ `Watson AI` จากนั้นเราจะส่งออกไฟล์**

**ในการตั้งค่า ให้ไปที่ `cloud.ibm.com` จากนั้นไปที่ตัวเลือก 'หมวดหมู่' เลือกหมวดหมู่ 'การเรียนรู้ของเครื่องและ AI' จากนั้นเลือกหมวดหมู่ 'นักแปลภาษา' ใหม่ หน้าต่างป๊อปอัปตามค่าเริ่มต้น เวอร์ชัน `lite` จะถูกเลือกและไม่เป็นไร เนื่องจากเป็นเวอร์ชันฟรีและเราจะใช้สิ่งนั้น คลิกที่ `create` และบริการจะถูกสร้างขึ้นให้เรา จากนั้นเราจะได้รับ คีย์ `API` ดังนั้นเราจะใช้คีย์ `API` เพื่อทำสิ่งต่างๆ ต่อไป**

## 1. Authenticate
```
api_key = ''<Enter your API KEY>'
url = ''<Enter your API URL>'
```

## 2.Translate
**ตอนนี้เราต้องอ้างถึงเอกสารประกอบ `Language Translator` เนื่องจากมีภาษาจำนวนมากและเราจำเป็นต้องระบุว่าเราต้องการแปลข้อความเป็นภาษาใด เพื่อให้สามารถอ้างอิงได้ <a href = " https://cloud.ibm.com/docs/language-translator?topic=language-translator-translation-models">ที่นี่</a> ตัวอย่างเช่น หากเราต้องการแปลข้อความจาก `english-thai` ที่เราใช้ บริการ "en-th" โดยที่ "en" หมายถึง "ภาษาอังกฤษ" และ "th" หมายถึง "ไทย" ดังนั้นเราจึงตั้งค่า "model_id" ของเรา "แปลจากโค้ด - แปลเป็นโค้ด" นี่คือรายการ ของภาษาที่คุณสามารถแปลจากภาษาหนึ่งไปยังอีกภาษาหนึ่งได้ เพียงแค่เราต้องตั้งรหัสตรงนั้น ดังรูป ↓ กรณีภาษาอังกฤษ-ไทย รหัสคือ `en-th` เหมือนกับการตั้งรหัสเป็น ตามข้อกำหนด**

<table>
            <caption>Table 1. Translatable languages</caption>
            <thead>
              <tr class="doc-tr-even">
                <th>Language</th>
                <th style="text-align:center">Language code</th>
                <th>Language</th>
                <th style="text-align:center">Language code</th>
              </tr>
            </thead>
            <tbody>
              <tr class="doc-tr-odd">
                <td><a href="#arabic">Arabic</a></td>
                <td style="text-align:center"><code>ar</code></td>
                <td><a href="#korean">Korean</a></td>
                <td style="text-align:center"><code>ko</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#basque">Basque</a> <strong>[1]</strong></td>
                <td style="text-align:center"><code>eu</code></td>
                <td><a href="#latvian">Latvian</a></td>
                <td style="text-align:center"><code>lv</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#bengali">Bengali</a></td>
                <td style="text-align:center"><code>bn</code></td>
                <td><a href="#lithuanian">Lithuanian</a></td>
                <td style="text-align:center"><code>lt</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#bosnian">Bosnian</a></td>
                <td style="text-align:center"><code>bs</code></td>
                <td><a href="#malay">Malay</a></td>
                <td style="text-align:center"><code>ms</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#bulgarian">Bulgarian</a></td>
                <td style="text-align:center"><code>bg</code></td>
                <td><a href="#malayalam">Malayalam</a></td>
                <td style="text-align:center"><code>ml</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#catalan">Catalan</a> <strong>[1]</strong></td>
                <td style="text-align:center"><code>ca</code></td>
                <td><a href="#maltese">Maltese</a></td>
                <td style="text-align:center"><code>mt</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#chinese-simplified">Chinese (Simplified)</a></td>
                <td style="text-align:center"><code>zh</code></td>
                <td><a href="#montenegrin">Montenegrin</a> <strong>[2]</strong></td>
                <td style="text-align:center"><code>cnr</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#chinese-traditional">Chinese (Traditional)</a></td>
                <td style="text-align:center"><code>zh-TW</code></td>
                <td><a href="#nepali">Nepali</a></td>
                <td style="text-align:center"><code>ne</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#croatian">Croatian</a></td>
                <td style="text-align:center"><code>hr</code></td>
                <td><a href="#norwegian-bokmal">Norwegian Bokmål</a></td>
                <td style="text-align:center"><code>nb</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#czech">Czech</a></td>
                <td style="text-align:center"><code>cs</code></td>
                <td><a href="#polish">Polish</a></td>
                <td style="text-align:center"><code>pl</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#danish">Danish</a></td>
                <td style="text-align:center"><code>da</code></td>
                <td><a href="#portuguese">Portuguese</a></td>
                <td style="text-align:center"><code>pt</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#dutch">Dutch</a></td>
                <td style="text-align:center"><code>nl</code></td>
                <td><a href="#romanian">Romanian</a></td>
                <td style="text-align:center"><code>ro</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#english">English</a></td>
                <td style="text-align:center"><code>en</code></td>
                <td><a href="#russian">Russian</a></td>
                <td style="text-align:center"><code>ru</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#estonian">Estonian</a></td>
                <td style="text-align:center"><code>et</code></td>
                <td><a href="#serbian">Serbian</a> <strong>[3]</strong></td>
                <td style="text-align:center"><code>sr</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#finnish">Finnish</a></td>
                <td style="text-align:center"><code>fi</code></td>
                <td><a href="#sinhala">Sinhala</a></td>
                <td style="text-align:center"><code>si</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#french">French</a></td>
                <td style="text-align:center"><code>fr</code></td>
                <td><a href="#slovak">Slovak</a></td>
                <td style="text-align:center"><code>sk</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#french-canadian">French (Canadian)</a></td>
                <td style="text-align:center"><code>fr</code></td>
                <td><a href="#slovenian">Slovenian</a></td>
                <td style="text-align:center"><code>sl</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#german">German</a></td>
                <td style="text-align:center"><code>de</code></td>
                <td><a href="#spanish">Spanish</a></td>
                <td style="text-align:center"><code>es</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#greek">Greek</a></td>
                <td style="text-align:center"><code>el</code></td>
                <td><a href="#swedish">Swedish</a></td>
                <td style="text-align:center"><code>sv</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#gujarati">Gujarati</a></td>
                <td style="text-align:center"><code>gu</code></td>
                <td><a href="#tamil">Tamil</a></td>
                <td style="text-align:center"><code>ta</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#hebrew">Hebrew</a></td>
                <td style="text-align:center"><code>he</code></td>
                <td><a href="#telugu">Telugu</a></td>
                <td style="text-align:center"><code>te</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#hindi">Hindi</a></td>
                <td style="text-align:center"><code>hi</code></td>
                <td><a href="#thai">Thai</a></td>
                <td style="text-align:center"><code>th</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#hungarian">Hungarian</a></td>
                <td style="text-align:center"><code>hu</code></td>
                <td><a href="#turkish">Turkish</a></td>
                <td style="text-align:center"><code>tr</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#irish">Irish</a></td>
                <td style="text-align:center"><code>ga</code></td>
                <td><a href="#ukrainian">Ukrainian</a></td>
                <td style="text-align:center"><code>uk</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#indonesian">Indonesian</a></td>
                <td style="text-align:center"><code>id</code></td>
                <td><a href="#urdu">Urdu</a></td>
                <td style="text-align:center"><code>ur</code></td>
              </tr>
              <tr class="doc-tr-even">
                <td><a href="#italian">Italian</a></td>
                <td style="text-align:center"><code>it</code></td>
                <td><a href="#vietnamese">Vietnamese</a></td>
                <td style="text-align:center"><code>vi</code></td>
              </tr>
              <tr class="doc-tr-odd">
                <td><a href="#japanese">Japanese</a></td>
                <td style="text-align:center"><code>ja</code></td>
                <td><a href="#welsh">Welsh</a></td>
                <td style="text-align:center"><code>cy</code></td>
              </tr>
            </tbody>
          </table>
          
![mobile (1)](https://user-images.githubusercontent.com/79361511/207608676-9ea4af12-2ce5-4a21-b9e4-2143592b8ed0.gif)



