# การทดลองสัปดาห์ที่ 5.1 #
## ศึกษา data structure  และ methods ของ predefined type ในภาษา C#  ##


### Learning Outcome ###
1. นักศึกษารู้จัก predefined type และบอกได้ว่ามีอะไรบ้าง
2. นักศึกษารู้จักองค์ประกอบของ predefined type แต่ละชนิดและสามารถสร้างแผนภาพอธิบาย type เหล่านั้นได้

### ความรู้เบื้องต้น ###
#### 1.  Predefined type ในภาษา C# ####

Predefined type ในภาษา C# มีอยู่ด้วยกัน 16 ชนิด (สำหรับคนที่ update เป็น C# version 9 แล้ว จะมี 18 ชนิด) ดังรูปที่ 1


![](./Pictures/PredefinedType.png)


<p align = "center"> <b>รูปที่ 1</b>  predefined type ในภาษา C# </p>

#### 2. การเข้าถึง predefined type โดยใช้ Visual Studio IDE ####
เราสามารถอาศัยเครื่องมือใน text editor ของ Visual Studio เข้าถึงนิยามของ predefined type ได้โดยการกดปุ่ม F12 หรือ กดปุ่ม Ctrl บนคีย์บอร์ดแล้วใช้เมาส์คลิกที่ขื่อของ Type นั้นๆ

##### ลำดับขั้นการทดลอง #####

1. สร้าง console project ใน Visual studio สมมติว่าตั้งชื่อ project เป็น `Week05_Lab1`



2. แก้ไขไฟล์ `program.cs` มีเนื้อหาดังต่อไปนี้


```cs
class Program
{
    sbyte sb;
    byte bt;
    short sh;
    ushort ush;
    int ii;
    uint ui;
    long lo;
    ulong ul;
    float fl;
    double db;
    bool bl;
    char ch;
    decimal de;

    object ob;
    string st;
    dynamic dy;

    static void Main(string[] args)
    {

    }
}
```

<p align = "center"> <b>รูปที่ 2 </b> Source code  ของ program.cs</p>


3. กดปุ่ม Ctrl แล้วใช้เมาส์คลิกที่ `sbyte` โปรแกรม Visual Studio จะเปิดไฟล์ใหม่ขึ้นมา ซื่งมือเนื้อหาของ `System.Sbyte`

![รูปที่ 2](./Pictures/Lab5_1_Pic2.png)


จะสังเกตได้ว่าในบรรทัดที่ 12 มีการสร้าง type ของข้อมูลเป็น `struct` ซึ่งมีการ สืบทอดมาจาก `Interface` หลายชนิด (จะได้เรียนเรื่อง `interface` ในภายหลัง)

ในบรรทัดที่ 18 และ 22 มีตัวแปรแบบ `public const SByte` จำนวนสองตัว ซึ่งทำหน้าที่บอกค่าสูงสุด (`MaxValue`) และค่าต่ำสุด  (`MinValue`) ที่สามารถเก็บในตัวแปรชนิดนี้ 

จากค่า `MaxValue`  และ   `MinValue` ทำให้เรารู้ได้ว่าตัวแปรที่สร้างจาก type นี้มีขนาด 8 บิตแบบคิดเครื่องหมาย นั่นคือต้องใช้บิดซ้ายสุดจำนวน 1 บิตเป็นตัวเก็บเครื่องหมาย (ถ้าบิตนี้มีค่า 0 คือจำนวนเต็มบวก ถ้าเป็น 1 จะเป็นจำนวนเต็มลบ) ดังนั้นจึงสามารถมีข้อมูลได้ 7 บิต (แทนค่าเป็นเลขฐานสิบได้ 0-127)

`1 0000000` ถึง `1 1111111` เป็นค่าลบ

`0 0000000` ถึง `0 1111111` เป็นค่าบวก


บรรทัดที่ 27 ถึง 338 จะเป็น methods ของชนิดข้อมูลนี้ ทำให้เรารู้ว่าสามารถทำอะไรกับชนิดข้อมูลนี้ได้บ้าง  

ถ้าลองคลิ่ folding โดยการคลิกที่เครื่องหมาย [+] เราจะเห็นข้อความอธิบายอยู่ใน comment ดังรูปที่ 3

![รูปที่ 3](./Pictures/Lab5_1_Pic3.png)

<p align = "center"> <b>รูปที่ 3</b> คำอธิบาย method ของ SByte </p>

4. วาดไดอะแกรมของ type นี้ด้วย plantuml

``` puml
@startuml
class SByte
{
  + Maxvalue : SByte
  + Minvalue : SByte

  + Parse(...) : SByte 
  + TryParse(...) : SByte
  + CompareTo(...) : SByte
  + Equals(...) : bool
  + GatHashCode() : int
  + GetTypeCode() : TypeCode
  + ToString(...) : string
}
@enduml
```

เมื่อ render ด้วยโปรแกรม plantuml แล้วจะได้คลาสไดอะแกรมดังนี้

![รูปที่ 3](./Pictures/SByte_uml.png)

<p align = "center"> <b>รูปที่ 4</b> diagram สำหรับ SByte </p>


----------
__หมายเหตุ__ 

รูปแบบของการเขียนรายละเอียดของตัวแปรและ function ใน class diagram คือ
```
< +|-|# > name [ : < return-type > ]
```
เมื่อ
```
+ คือการเข้าถึงแบบ public
- คือการเข้าถึงแบบ private
# คือการเข้าถึงแบบ protected

< > หมายถึงเป็นส่วนที่ต้องมี (required)
[ ] หมายถึงเป็นส่วนที่ไม่ต้องก็ได้ (optional)

เช่น 
 + Maxvalue : SByte     //  ในกรณีที่ต้องการระบุให้ชัดเจนเนื่องจากรู้ชนิดล่วงหน้าแล้ว
 หรือ 
 + Maxvalue             // ในกรณีที่ยังไม่รู้ชนิดล่วงหน้า 

```
ในกรณีที่ชื่อฟังก์ชันเหมือนกันแต่มี parameter ต่างกันให้เขียน parameter  เป็น (...) แล้วใช้ฟังก์ชันเดียวเท่านั้น

----------

## แบบฝึกหัด ##

เขียนโค้ด plantuml สำหรับ type ชนิดอื่นๆ โดยใช้วิธีเดียวกันกับขั้นตอนที่ 3  เพื่อสร้าง diagram สำหรับ predefined type ทุกชนิด

# 1. Byte
``` puml
@startuml
class Byte {
    + MaxValue : Byte
    + MinValue : Byte
    + Parse(...) : Byte
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : string
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331537-28adbae6-d485-4ed4-92cc-8152f87a8946.png)

# 2. short (Int16)
``` puml
@startuml
class Int16 {
    + Maxvalue : Int16
    + Minvalue : Int16
    + Parse(...) : Int16
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : string
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331549-80cceef1-1198-470e-aec1-24087f4f2d2c.png)

# 3. ushort (UInt16)
``` puml
@startuml
class UInt16 {
    + Maxvalue : UInt16
    + Minvalue : UInt16
    + Parse(...) : UInt16
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : string
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331565-215c6b41-b147-4c91-8dd2-6373cc46881a.png)

# 4. int (Int32)
``` puml
@startuml
class Int32{
    + Minvalue : Int32
    + Maxvalue : Int32
    + Parse(...) : Int32
    + TryParse(...) : bool
    + CompareTo(...) : Int32
    + Equals(...) : bool
    + GetHashCode() : Int32
    + GetTypeCode() : TypeCode
    + ToString(...) : string
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331585-2c2bba76-2610-445e-83a3-5157fa2eee1f.png)

# 5. uint (UInt32)
``` puml
@startuml
class UInt32 {
    + Maxvalue : UInt32
    + Minvalue : UInt32
    + Parse(...) : UInt32
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : string
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331599-d4320b35-3592-419e-b843-1982e9edd799.png)

# 6. long (Int64)
``` puml
@startuml
class Int64 {
    + Maxvalue : Int64
    + Minvalue : Int64
    + Parse(...) : Int64
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : string
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331606-23fa7082-fdcf-4596-bb0b-c9a492885963.png)

# 7. ulong (UInt64)
``` puml
@startuml
class Int64 {
    + Maxvalue : Int64
    + Minvalue : Int64
    + Parse(...) : Int64
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : string
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331616-c05debca-31d1-4918-8333-3ab74a7884ac.png)

# 8. float (Single)
``` puml
@startuml
class Single {
    + MinValue : Single
    + Epsilon : Single
    + MaxValue : Single
    + PositiveInfinity : Single
    + NegativeInfinity : Single
    + NaN : Single
    + IsInfinity(...) : bool
    + IsNaN(...) : bool
    + IsNegativeInfinity(...) : bool
    + IsPositiveInfinity(...) : bool
    + Parse(...) : Single
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : ToString
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331629-47c84b59-8e35-40fb-be02-0e69c02125d2.png)

# 9. double
``` puml
@startuml
class Double {
    + MinValue : Double
    + MaxValue : Double
    + Epsilon : Double
    + NegativeInfinity : Double
    + PositiveInfinity : Double
    + NaN : Double
    + IsInfinity(...) : bool
    + IsNaN(...) : bool
    + IsNegativeInfinity(...) : bool
    + IsPositiveInfinity(...) : bool
    + Parse(...) : Double
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : ToString
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331645-507c2cd7-faba-4b4c-a970-b78671364349.png)

# 10. bool
``` puml
@startuml
class Boolean {
    + TrueString : string
    + FalseString : string
    + Parse(...) : Boolean
    + TryParse(...) : Boolean
    + CompareTo(...) : int
    + Equals(...) : Boolean
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : string 
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331659-931ca205-9adf-44be-8b21-b114c4d0c7c5.png)

# 11. char
``` puml
@startuml
class Char {
    + MaxValue : Char
    + MinValue : Char
    + ConvertFromUtf32(...) : string
    + ConvertToUtf32(...) : int
    + GetNumericValue(...) : double
    + GetUnicodeCategory(...) : UnicodeCategory
    + IsControl(...) : bool
    + IsDigit(...) : bool
    + IsHighSurrogate(...) : bool
    + IsLetter(...) : bool
    + IsLetterOrDigit(...) : bool
    + IsLower(...) : bool
    + IsLowSurrogate(...) : bool
    + IsNumber(...) : bool
    + IsPunctuation(...) : bool
    + IsSeparator(...) : bool
    + IsSurrogate(...) : bool
    + IsSurrogatePair(...) : bool
    + IsSymbol(...) : bool
    + IsUpper(...) : bool
    + IsWhiteSpace(...) : bool
    + Parse(...) : Char
    + ToLower(...) : Char
    + ToLowerInvariant(...) : Char
    + ToString(...) : string
    + ToUpper(...) : Char
    + ToUpperInvariant(...) : Char
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331667-9e34520d-4bab-4154-9124-a44141dbf8a6.png)

# 12. decimal
``` puml
@startuml
class Decimal {
    + Zero : Decimal
    + One : Decimal
    + MinusOne : Decimal
    + MaxValue : Decimal
    + MaxValue : Decimal
    + int[] bits : Decimal
    + float value : Decimal
    + ulong value : Decimal
    + double value : Decimal
    + uint value : Decimal
    + int value : Decimal
    + int lo, int mid, int hi, bool isNegative, byte scale : Decimal
    + Add(...) : Decimal
    + Ceiling(...) : Decimal
    + Ceiling(...) : Decimal
    + Compare(...) : int
    + Divide(...) : Decimal
    + Equals(...) : bool
    + Floor(...) : Decimal
    + FromOACurrency(...) : Decimal
    + GetBits(...) : int[]
    + Multiply(...) : Decimal
    + Negate(...) : Decimal
    + Parse(...) : Decimal
    + Remainder(...) : Decimal
    + Round(...) : Decimal
    + Subtract(...) : Decimal
    + ToByte(...) : byte
    + ToDouble(...) : double
    + ToInt16(...) : short
    + ToInt32(...) : int
    + ToInt64(...) : long
    + ToOACurrency(...) : long
    + ToSByte(...) : sbyte
    + ToSingle(...) : float
    + ToUInt16(...) : ushort
    + ToUInt32(...) : uint
    + ToUInt64(...) : ulong
    + Truncate(...) : Decimal
    + TryParse(...) : bool
    + CompareTo(...) : int
    + Equals(...) : bool
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + ToString(...) : string
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331675-81d912c6-cab3-44c7-ac3f-c23ad3e7454c.png)

# 13. Object
``` puml
@startuml
class Object {
    + Object
    + Equals(...) : bool
    + ReferenceEquals(...) : bool
    + GetHashCode() : int
    + GetType() : Type
    + ToString() : string
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331682-04a0951d-3ac4-4081-81da-904226fefdfe.png)

# 14. string
``` puml
@startuml
class String {
    + Empty : String
    + char[] value : String
    + sbyte* value : String
    + char* value : String
    + char c, int count : String
    + char[] value, int startIndex, int length : String
    + sbyte* value, int startIndex, int length : String
    + char* value, int startIndex, int length : String
    + sbyte* value, int startIndex, int length, Encoding enc : String
    + Length : int
    + Compare(...) : int
    + CompareOrdinal(...) : int
    + Concat(...) : String
    + Copy(...) : String
    + Equals(...) : bool
    + Format(...) : String
    + Intern(...) : String
    + IsInterned(...) : String
    + IsNullOrEmpty(...) : bool
    + IsNullOrWhiteSpace(...) : bool
    + Join(...) : String
    + Clone() : object
    + CompareTo(...) : int
    + Contains(...): bool
    + CopyTo(...) : void
    + EndsWith(...) : bool
    + GetEnumerator() : CharEnumerator
    + GetHashCode() : int
    + GetTypeCode() : TypeCode
    + IndexOf(...) : int
    + IndexOfAny(...) : int
    + Insert(...) : String
    + IsNormalized() : bool
    + LastIndexOf(...) : int
    + LastIndexOfAny(...) : int
    + Normalize() : String
    + PadLeft(...) : String
    + PadRight(...)  : String
    + Remove(...) : String
    + Replace(...) : String
    + Split(...) : String[]
    + StartsWith(...) : bool
    + Substring(...) : String
    + ToCharArray(...) : char
    + ToLower(...) : String
    + ToLowerInvariant() : String
    + ToString(...) : String
    + ToUpper(...) : String
    + ToUpperInvariant() : String
    + Trim() : String
    + TrimEnd(...) : String
    + TrimStart() : String
}
@enduml
```
![image](https://user-images.githubusercontent.com/115037574/218331691-d0da2a93-89c2-4143-a7d6-2d7c5a011486.png)
