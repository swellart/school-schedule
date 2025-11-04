# school-schedule

## **CSV Column Format Guide:**

| Column | Format | Example | Notes |
|--------|--------|---------|-------|
| **ID** | Number | `1` | Auto-generated if empty |
| **Subject** | Text | `Mathematics` | Required |
| **Teacher** | Text | `Mr. Smith` | Required |
| **Group/Class** | Text | `Grade 10A` | Optional |
| **Color** | Hex code | `#3b82f6` | Default `#3b82f6` if empty |
| **Required Days** | Day names, semicolon-separated | `Monday;Wednesday;Friday` | Use exact day names |
| **Required Time Slots** | Slot IDs, semicolon-separated | `1;2;3` | Must match time slot IDs |
| **Required Classroom** | Classroom ID | `1` | Must match classroom ID |
| **Preferred Days** | Day names, semicolon-separated | `Tuesday;Thursday` | Use exact day names |
| **Preferred Time Slots** | Slot IDs, semicolon-separated | `2;3` | Must match time slot IDs |
| **Preferred Classroom** | Classroom ID | `2` | Must match classroom ID |
| **Unavailable Days** | Day names, semicolon-separated | `Friday` | Use exact day names |
| **Unavailable Time Slots** | Slot IDs, semicolon-separated | `4` | Must match time slot IDs |
| **Max Per Day** | Number | `2` | Default is `2` |
| **Can Combine With** | Subject IDs, semicolon-separated | `2;3` | IDs of other subjects |

## **Important Notes:**

### **Day Names** - Must be EXACT:
- `Monday`
- `Tuesday`
- `Wednesday`
- `Thursday`
- `Friday`

### **Time Slot IDs** - Find them by exporting Time Slots CSV first:
1. Go to "Classrooms & Times" tab
2. Click "Export CSV" under Time Slots
3. Look at the ID column
4. Use those numbers in your subjects CSV

Example Time Slots CSV:
```
ID,Start Time,End Time
1,08:00,09:00
2,09:00,10:00
3,10:00,11:00
4,11:00,12:00
```

### **Classroom IDs** - Find them by exporting Classrooms CSV:
1. Go to "Classrooms & Times" tab
2. Click "Export CSV" under Classrooms
3. Look at the ID column

Example Classrooms CSV:
```
ID,Name
1,Room 101
2,Room 102
3,Lab A
```

## **Full Example Google Sheet:**

```
ID,Subject,Teacher,Group/Class,Color,Required Days,Required Time Slots,Required Classroom,Preferred Days,Preferred Time Slots,Preferred Classroom,Unavailable Days,Unavailable Time Slots,Max Per Day,Can Combine With
1,Mathematics,Mr. Smith,Grade 10A,#3b82f6,Monday;Wednesday,,1,,,,,Friday,,2,
2,Physics,Dr. Brown,Grade 10A,#f59e0b,,1;2,3,Tuesday;Thursday,,,,,3,1
3,English,Ms. Johnson,Grade 10B,#10b981,,,,,2;3,2,,,2,
4,PE,Mr. Davis,Combined,#ef4444,Friday,4,,,,,,Monday;Tuesday,,1,2;3
```

**Explanation:**
- **Row 1 (Math)**: Must be Monday or Wednesday, must use Room 101 (ID=1), unavailable Friday, max 2/day
- **Row 2 (Physics)**: Must use time slots 1-2 (08:00-10:00), must use Lab A (ID=3), prefers Tue/Thu, max 3/day, can combine with Math (ID=1)
- **Row 3 (English)**: Prefers time slots 2-3, prefers Room 102 (ID=2), max 2/day
- **Row 4 (PE)**: Must be Friday at slot 4, unavailable Mon/Tue, can combine with Physics(2) & English(3)

## **Pro Tip - Workflow:**

1. **First**, export your current Classrooms and Time Slots to see their IDs
2. **Then**, create your Subjects CSV using those IDs
3. **Import** the Subjects CSV

This way you'll have the correct IDs! 🎯
