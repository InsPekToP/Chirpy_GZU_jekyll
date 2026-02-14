---
title: Добавление бафа всем участникам пати
date: 2026-02-12 12:00:00 +0200
categories: [Разделы, Lineage 2]
tags: [lineage 2]     
---

# 📌 Добавление бафа всем участникам пати

Реализован баф, который накладывается на всех участников группы.  
Уровень бафа автоматически зависит от количества игроков в пати.  
Эффект бафа увеличивает **персональный дроп**.

---

## 🛡 Skill: Bond of Warriors — Узы воинов

### 🇬🇧 Skill Description (EN)
> Fills the character with the energy of unity.  
> Personal drop is increased by #.  
> The effect’s strength depends on the number of party members.

### 🇷🇺 Skill Description (RU)
> Наполняет персонажа энергией единства.  
> Персональный дроп увеличен на #.  
> Сила эффекта зависит от численности группы.

---

## ⚙️ Параметры скилла

- **Skill ID:** `3665`
- **Количество уровней:** `8`
- **Тип:** Buff
- **Время действия:** 36000 сек

### 📈 Уровни и бонус к дропу

| Уровень | Бонус к дропу |
|----------|----------------|
| 1 | +15% |
| 2 | +30% |
| 3 | +45% |
| 4 | +60% |
| 5 | +75% |
| 6 | +90% |
| 7 | +105% |
| 8 | +120% |

---

## 🧩 Skill XML

```xml
<skill id="3665" levels="8" name="Bond of Warriors">
    <table name="#dropRate"> 
        1.15 1.3 1.45 1.6 1.75 1.9 2.05 2.20 
    </table>

    <set name="power" val="0.0" />
    <set name="target" val="TARGET_ONE" />
    <set name="reuseDelay" val="0" />
    <set name="hitTime" val="100" />
    <set name="skillType" val="BUFF" />
    <set name="isMagic" val="true" />
    <set name="operateType" val="OP_ACTIVE" />
    <set name="castRange" val="400" />
    <set name="effectRange" val="900" />

    <for>
        <effect count="1" name="Buff" time="36000" val="0">
            <mul order="0x60" stat="rateDropCount" val="#dropRate"/>
        </effect>
    </for>
</skill>
```