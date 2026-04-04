# USS Selectors (Unity Style Sheets)

## 1. Selector theo class
```css
.my-button {
    background-color: red;
}
```

Áp dụng cho:
```xml
<Button class="my-button"/>
```

---

## 2. Selector theo name (giống id)
```css
#loginBtn {
    color: white;
}
```

Áp dụng cho:
```xml
<Button name="loginBtn"/>
```

---

## 3. Selector theo type (loại element)
```css
Button {
    font-size: 18px;
}
```

Áp dụng cho tất cả Button

---

## 4. Selector lồng (descendant)
```css
.container Label {
    color: yellow;
}
```

Label nằm trong `.container`

---

## 5. Selector con trực tiếp
```css
.container > Label {
    color: green;
}
```

Chỉ áp dụng cho con cấp 1

---

## 6. Multiple class
```css
.btn.primary {
    background-color: blue;
}
```

Áp dụng cho:
```xml
<Button class="btn primary"/>
```

---

## 7. Pseudo states (trạng thái)
```css
Button:hover {
    background-color: gray;
}

Button:active {
    background-color: red;
}

Button:disabled {
    opacity: 0.5;
}
```

---

## 8. First child
```css
Label:first-child {
    color: red;
}
```

(Lưu ý: hỗ trợ hạn chế)

---

## 9. Universal selector
```css
* {
    font-size: 14px;
}
```

Áp dụng toàn bộ UI

---

## 10. Selector kết hợp
```css
#menu .btn:hover {
    background-color: orange;
}
```

---

## 11. Ví dụ hoàn chỉnh

### UXML
```xml
<ui:VisualElement name="menu" class="container">
    <ui:Button class="btn primary" text="Play"/>
    <ui:Button class="btn" text="Exit"/>
</ui:VisualElement>
```

### USS
```css
.container {
    flex-direction: column;
}

.btn {
    background-color: gray;
}

.btn.primary {
    background-color: green;
}

#menu .btn:hover {
    background-color: yellow;
}
```

---

## 12. Những thứ USS KHÔNG hỗ trợ
- Attribute selector (`[type="..."]`)
- CSS Grid
- Animation CSS
- Selector nâng cao như web

---

## 13. Lưu ý quan trọng

### Class phải add đúng cách trong code
```csharp
element.AddToClassList("btn");
```

### Phân biệt name và class
```xml
name="abc"   <!-- dùng #abc -->
class="abc"  <!-- dùng .abc -->
```

---

## Kết luận
- USS giống CSS nhưng đơn giản hơn  
- Dùng tốt cho UI game (menu, HUD, setting)  
- Nên ưu tiên class + flex layout  
