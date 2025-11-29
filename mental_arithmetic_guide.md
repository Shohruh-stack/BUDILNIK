# Mental Arifmetika Dasturini Yaratish Uchun Yo'riqnoma

Ushbu hujjatda mental arifmetikaning abakusda hisoblash usullari ("Kichik do'st" va "Katta do'st") bo'yicha formulalar va ularni dasturiy ta'minotda qo'llash uchun algoritmik yondashuvlar keltirilgan.

## 1. Abakus Asoslari

Dastur mantig'ini qurishdan oldin, abakusning virtual modelini tushunish kerak.

- **Ustun (Column/Rod):** Dasturda har bir xonani (birlar, o'nlar, yuzlar va hokazo) ifodalovchi o'zgaruvchi yoki obyekt. Har bir ustun 0 dan 9 gacha bo'lgan qiymatni saqlaydi.
- **Munchoqlar:** Har bir ustunning qiymatini aniqlash uchun virtual munchoqlar holatini kuzatish mumkin:
  - **Yuqori munchoq (qiymati 5):** `is_upper_bead_active` (boolean)
  - **Pastki munchoqlar (har birining qiymati 1):** `lower_beads_count` (0 dan 4 gacha butun son)
- **Ustun qiymatini hisoblash:** `value = (is_upper_bead_active ? 5 : 0) + lower_beads_count`

## 2. "Kichik do'st" Usuli (5 ga asoslangan formulalar)

Bu usul bir xona (ustun) ichida, qo'shish yoki ayirish uchun pastki munchoqlar yetarli bo'lmaganda qo'llaniladi.

### Qo'shish uchun formulalar: `+X = +5 - (5-X)`
*(5 ni qo'shib, X ning do'stini ayirish)*

| Formula       | Sharti                                                         | Amal                                           |
|---------------|----------------------------------------------------------------|------------------------------------------------|
| **`+4 = +5 - 1`** | `ustun_qiymati` {1,2,3,4} ichida (`ustun_qiymati % 5 + 4 >= 5`)   | Yuqori munchoqni faollashtir, 1 pastki munchoqni pasaytir |
| **`+3 = +5 - 2`** | `ustun_qiymati` {2,3,4} ichida (`ustun_qiymati % 5 + 3 >= 5`)   | Yuqori munchoqni faollashtir, 2 pastki munchoqni pasaytir |
| **`+2 = +5 - 3`** | `ustun_qiymati` {3,4} ichida (`ustun_qiymati % 5 + 2 >= 5`)     | Yuqori munchoqni faollashtir, 3 pastki munchoqni pasaytir |
| **`+1 = +5 - 4`** | `ustun_qiymati` {4} ichida (`ustun_qiymati % 5 + 1 >= 5`)         | Yuqori munchoqni faollashtir, 4 pastki munchoqni pasaytir |

### Ayirish uchun formulalar: `-X = -5 + (5-X)`
*(5 ni ayirib, X ning do'stini qo'shish)*

| Formula       | Sharti                         | Amal                                            |
|---------------|--------------------------------|-------------------------------------------------|
| **`-4 = -5 + 1`** | `ustun_qiymati` >= 5 va `pastki_munchoqlar` soni < 4 | Yuqori munchoqni o'chir, 1 pastki munchoqni qo'sh |
| **`-3 = -5 + 2`** | `ustun_qiymati` >= 5 va `pastki_munchoqlar` soni < 3 | Yuqori munchoqni o'chir, 2 pastki munchoqni qo'sh |
| **`-2 = -5 + 3`** | `ustun_qiymati` >= 5 va `pastki_munchoqlar` soni < 2 | Yuqori munchoqni o'chir, 3 pastki munchoqni qo'sh |
| **`-1 = -5 + 4`** | `ustun_qiymati` >= 5 va `pastki_munchoqlar` soni < 1 | Yuqori munchoqni o'chir, 4 pastki munchoqni qo'sh |

## 3. "Katta do'st" Usuli (10 ga asoslangan formulalar)

Bu usul joriy ustunda amalni bajarishning iloji bo'lmaganda (na to'g'ridan-to'g'ri, na "Kichik do'st" usuli bilan) qo'llaniladi va o'zidan oldingi (chapdagi) kattaroq xonani o'z ichiga oladi.

### Qo'shish uchun formulalar: `+X = -(10-X) + 10`
*(Joriy ustundan X ning do'stini ayirib, chapdagi ustunga 1 qo'shish)*

| Formula       | Sharti                      | Amal                                              |
|---------------|-----------------------------|---------------------------------------------------|
| **`+9 = -1 + 10`** | `ustun_qiymati + 9 > 9`      | Joriy ustundan 1 ni ayir, chapdagi ustunga 1 qo'sh |
| **`+8 = -2 + 10`** | `ustun_qiymati + 8 > 9`      | Joriy ustundan 2 ni ayir, chapdagi ustunga 1 qo'sh |
| **`+7 = -3 + 10`** | `ustun_qiymati + 7 > 9`      | Joriy ustundan 3 ni ayir, chapdagi ustunga 1 qo'sh |
| **`+6 = -4 + 10`** | `ustun_qiymati + 6 > 9`      | Joriy ustundan 4 ni ayir, chapdagi ustunga 1 qo'sh |
| **`+5 = -5 + 10`** | `ustun_qiymati + 5 > 9`      | Joriy ustundan 5 ni ayir, chapdagi ustunga 1 qo'sh |
| **`+4 = -6 + 10`** | `ustun_qiymati + 4 > 9`      | Joriy ustundan 6 ni ayir, chapdagi ustunga 1 qo'sh |
| **`+3 = -7 + 10`** | `ustun_qiymati + 3 > 9`      | Joriy ustundan 7 ni ayir, chapdagi ustunga 1 qo'sh |
| **`+2 = -8 + 10`** | `ustun_qiymati + 2 > 9`      | Joriy ustundan 8 ni ayir, chapdagi ustunga 1 qo'sh |
| **`+1 = -9 + 10`** | `ustun_qiymati + 1 > 9`      | Joriy ustundan 9 ni ayir, chapdagi ustunga 1 qo'sh |

### Ayirish uchun formulalar: `-X = -10 + (10-X)`
*(Chapdagi ustundan 1 ni ayirib, joriy ustunga X ning do'stini qo'shish)*

| Formula       | Sharti                  | Amal                                                |
|---------------|-------------------------|-----------------------------------------------------|
| **`-9 = -10 + 1`** | `ustun_qiymati < 9`    | Chapdagi ustundan 1 ni ayir, joriy ustunga 1 qo'sh   |
| **`-8 = -10 + 2`** | `ustun_qiymati < 8`    | Chapdagi ustundan 1 ni ayir, joriy ustunga 2 qo'sh   |
| **`-7 = -10 + 3`** | `ustun_qiymati < 7`    | Chapdagi ustundan 1 ni ayir, joriy ustunga 3 qo'sh   |
| **`-6 = -10 + 4`** | `ustun_qiymati < 6`    | Chapdagi ustundan 1 ni ayir, joriy ustunga 4 qo'sh   |
| **`-5 = -10 + 5`** | `ustun_qiymati < 5`    | Chapdagi ustundan 1 ni ayir, joriy ustunga 5 qo'sh   |
| **`-4 = -10 + 6`** | `ustun_qiymati < 4`    | Chapdagi ustundan 1 ni ayir, joriy ustunga 6 qo'sh   |
| **`-3 = -10 + 7`** | `ustun_qiymati < 3`    | Chapdagi ustundan 1 ni ayir, joriy ustunga 7 qo'sh   |
| **`-2 = -10 + 8`** | `ustun_qiymati < 2`    | Chapdagi ustundan 1 ni ayir, joriy ustunga 8 qo'sh   |
| **`-1 = -10 + 9`** | `ustun_qiymati < 1`    | Chapdagi ustundan 1 ni ayir, joriy ustunga 9 qo'sh   |

## 4. Dastur uchun Algoritmik Yondashuv

Har bir xona (birliklar, o'nliklar va h.k.) uchun qo'shish yoki ayirish amalini bajarayotganda, dastur quyidagi tartibda tekshirishi kerak:

1.  **To'g'ridan-to'g'ri hisoblash:**
    - Qo'shish/ayirish uchun joriy ustunda munchoqlar yetarlimi?
    - Agar ha bo'lsa, amalni bajaring va keyingi xonaga o'ting.
    - Agar yo'q bo'lsa, 2-qadamga o'ting.

2.  **"Kichik do'st" usulini qo'llash:**
    - Amal "Kichik do'st" formulalaridan biriga mos keladimi? (Yuqoridagi shartlarni tekshiring).
    - Agar ha bo'lsa, formulani qo'llang va keyingi xonaga o'ting.
    - Agar yo'q bo'lsa, 3-qadamga o'ting.

3.  **"Katta do'st" usulini qo'llash:**
    - Amal "Katta do'st" formulalaridan biriga mos keladimi?
    - Agar ha bo'lsa, formulani qo'llang (joriy va chapdagi ustunlarni o'zgartiring) va keyingi xonaga o'ting.

4.  **Kombinatsiyalangan usullar (Murakkab holatlar):**
    - Ba'zi hollarda (masalan, 6 ni qo'shish uchun `+1+5`), "Kichik" va "Katta" do'st formulalari birgalikda qo'llanilishi mumkin. Masalan, `+6 = +1 - 5 + 10`. Dasturning keyingi versiyalarida bu kabi holatlarni ham hisobga olish mumkin.

Ushbu yo'riqnoma sizning dasturingiz uchun mustahkam poydevor bo'lib xizmat qiladi. Har bir qoidani funksiyalar yoki metodlar orqali amalga oshirish dasturni modulli va tushunarli qiladi.
