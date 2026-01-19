# Flexbox Properties Reference Card

## Quick Lookup Guide for All Flex Properties Used in This Project

### Container Properties (Applied to Parent)

#### 1. `display: flex`
**Turns element into flex container**
```css
display: flex;
```
- Makes all direct children flex items
- Used in: navbar, hero, cards, footer

---

#### 2. `flex-direction`
**Controls main axis direction**
```css
flex-direction: row;      /* Default - left to right */
flex-direction: column;   /* Top to bottom */
flex-direction: row-reverse;
flex-direction: column-reverse;
```

| Value | Use Case | Example in Project |
|-------|----------|-------------------|
| `row` | Horizontal layout | Nav links, skill items |
| `column` | Vertical layout | Card content, hero content |

---

#### 3. `justify-content`
**Align items along main axis**
```css
justify-content: flex-start;      /* Align to start */
justify-content: flex-end;        /* Align to end */
justify-content: center;          /* Center items */
justify-content: space-between;   /* Space items apart */
justify-content: space-around;    /* Equal space around items */
justify-content: space-evenly;    /* Equal space between items */
```

| Value | Purpose | Project Use |
|-------|---------|------------|
| `center` | Center all items | Hero section, cards container |
| `space-between` | Max separation | Navigation (logo ↔ links) |
| `space-around` | Even spacing | Footer sections |
| `flex-start` | Align to start | Default behavior |
| `flex-end` | Align to end | Less common |

**Visual:**
```
space-between:   [item]                    [item]
space-around:     [item]        [item]        [item]
space-evenly:    [item]      [item]      [item]      [item]
center:                    [item] [item] [item]
```

---

#### 4. `align-items`
**Align items along cross axis**
```css
align-items: stretch;     /* Default - stretch to fill */
align-items: flex-start;  /* Align to start of cross axis */
align-items: flex-end;    /* Align to end of cross axis */
align-items: center;      /* Center on cross axis */
align-items: baseline;    /* Align to baseline */
```

| Value | Effect (if flex-direction: row) | Project Use |
|-------|--------------------------------|------------|
| `center` | Vertically center | Navigation, images |
| `stretch` | Fill container height | Card images |
| `flex-start` | Top alignment | Default |
| `flex-end` | Bottom alignment | Less common |

**Visual:**
```
Normal (stretch):    [████████]
                     [████████]
                     [████████]

Center:              [        ]
                     [████████]
                     [        ]

Flex-start:          [████████]
                     [████████]
                     [        ]
```

---

#### 5. `flex-wrap`
**Control wrapping of flex items**
```css
flex-wrap: nowrap;   /* All items on one line (default) */
flex-wrap: wrap;     /* Items wrap to next line */
flex-wrap: wrap-reverse;
```

| Value | Behavior | Project Use |
|-------|----------|------------|
| `wrap` | Items move to next line when space runs out | Cards, skills |
| `nowrap` | Force all items on one line | Navigation (with overflow) |

**Visual:**
```
nowrap:  [item1] [item2] [item3] [item4] [item5]

wrap:    [item1] [item2] [item3]
         [item4] [item5]
```

---

#### 6. `gap`
**Space between flex items**
```css
gap: 1rem;        /* Same gap on all sides */
gap: 1rem 2rem;   /* row-gap, column-gap */
row-gap: 1rem;
column-gap: 2rem;
```

| Usage | Project Use |
|-------|------------|
| `gap: 2rem;` | Card spacing, section spacing |
| `gap: 1rem;` | Smaller spacing, nav links |
| `gap: 0.8rem;` | Tight spacing, skill pills |

**Benefits:**
- ✓ No need to add margins to items
- ✓ Consistent spacing
- ✓ Easier responsive adjustments

---

#### 7. `flex-flow` (Shorthand)
**Combines flex-direction and flex-wrap**
```css
flex-flow: row wrap;
flex-flow: column wrap;
flex-flow: column nowrap;
```

---

### Item Properties (Applied to Children)

#### 8. `flex-basis`
**Default size of flex item before space distribution**
```css
flex-basis: auto;           /* Size based on content */
flex-basis: 300px;          /* Fixed width */
flex-basis: 50%;            /* Percentage of container */
flex-basis: calc(50% - 1rem); /* Calculated value */
```

**Project Examples:**
```css
/* 3-column layout */
flex-basis: calc(33.333% - 2rem);

/* 2-column layout */
flex-basis: calc(50% - 2rem);

/* Full width */
flex-basis: 100%;

/* Auto-sized skill item */
flex-basis: auto;
```

**Responsive Pattern:**
```css
/* Desktop */
.card { flex-basis: calc(33.333% - 2rem); }

/* Tablet */
@media (max-width: 1024px) {
  .card { flex-basis: calc(50% - 2rem); }
}

/* Mobile */
@media (max-width: 768px) {
  .card { flex-basis: 100%; }
}
```

---

#### 9. `flex-grow`
**How much item grows to fill available space**
```css
flex-grow: 0;  /* Don't grow (default) */
flex-grow: 1;  /* Grow equally with siblings */
flex-grow: 2;  /* Grow twice as much as siblings */
```

**Project Use:**
```css
.project-card {
    flex-grow: 1;  /* Cards expand to fill width */
}

.card-content {
    flex-grow: 1;  /* Content expands to fill card */
}
```

**Visual:**
```
flex-grow: 0;  [100px] [100px] [100px]    (empty space)

flex-grow: 1;  [150px] [150px] [150px]    (distributed evenly)
```

---

#### 10. `flex-shrink`
**How much item shrinks when space is tight**
```css
flex-shrink: 1;  /* Shrink equally (default) */
flex-shrink: 0;  /* Don't shrink */
flex-shrink: 2;  /* Shrink twice as much */
```

**Project Use:**
```css
.project-card {
    flex-shrink: 1;  /* Cards can shrink */
    min-width: 300px; /* But not smaller than 300px */
}
```

---

#### 11. `flex` (Shorthand)
**Combines flex-grow, flex-shrink, flex-basis**
```css
flex: 1;              /* flex-grow: 1, flex-shrink: 1, flex-basis: 0% */
flex: 0 1 auto;       /* Don't grow, shrink allowed, auto basis */
flex: 1 1 100%;       /* Grow, shrink, 100% basis */
```

**Equivalent:**
```css
flex: 1;

/* Is same as: */
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0%;
```

---

#### 12. `align-self`
**Override align-items for single item**
```css
align-self: auto;        /* Use align-items value */
align-self: flex-start;
align-self: center;
align-self: flex-end;
align-self: stretch;
```

---

#### 13. `order`
**Change visual order of items**
```css
order: -1;  /* Move before others */
order: 0;   /* Default */
order: 1;   /* Move after others */
```

---

## Common Patterns in This Project

### Pattern 1: Center Everything
```css
.container {
    display: flex;
    justify-content: center;   /* Center horizontally */
    align-items: center;       /* Center vertically */
}
```
**Used in:** Hero section, card images

---

### Pattern 2: Space Between (Logo + Nav)
```css
.navbar {
    display: flex;
    justify-content: space-between;  /* Logo left, links right */
    align-items: center;
}
```
**Used in:** Navigation bar

---

### Pattern 3: Vertical Stack with Gap
```css
.content {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
}
```
**Used in:** Hero content, card content, footer sections

---

### Pattern 4: Responsive Grid with Wrap
```css
.grid {
    display: flex;
    flex-wrap: wrap;
    gap: 2rem;
}

.grid-item {
    flex-basis: calc(33.333% - 2rem);  /* 3 columns */
    flex-grow: 1;
    min-width: 300px;
}

@media (max-width: 1024px) {
    .grid-item {
        flex-basis: calc(50% - 2rem);  /* 2 columns */
    }
}

@media (max-width: 768px) {
    .grid-item {
        flex-basis: 100%;  /* 1 column */
    }
}
```
**Used in:** Project cards, skill categories

---

### Pattern 5: Flowing Items
```css
.items {
    display: flex;
    flex-wrap: wrap;
    gap: 0.8rem;
}

.item {
    flex-basis: auto;  /* Size to content */
}
```
**Used in:** Skill pills, navigation links

---

### Pattern 6: Filling Item
```css
.container {
    display: flex;
    flex-direction: column;
}

.content {
    flex-grow: 1;  /* Expands to fill space */
}

.button {
    margin-top: auto;  /* Pushed to bottom */
}
```
**Used in:** Card content (button at bottom)

---

## Responsive Design Workflow

### 1. Mobile First (320px)
```css
.container {
    display: flex;
    flex-direction: column;  /* Stack everything */
    gap: 1rem;
}

.item {
    flex-basis: 100%;  /* Full width */
}
```

### 2. Add Tablet Breakpoint (768px)
```css
@media (min-width: 768px) {
    .item {
        flex-basis: calc(50% - 1rem);  /* 2 columns */
    }
}
```

### 3. Add Desktop Breakpoint (1024px)
```css
@media (min-width: 1024px) {
    .item {
        flex-basis: calc(33.333% - 2rem);  /* 3 columns */
    }
}
```

---

## Debugging Flexbox

### Issue: Items Not Aligning
**Check:**
```css
✓ display: flex; on parent?
✓ justify-content or align-items set?
✓ flex-direction: column changes cross axis?
```

### Issue: Items Not Wrapping
**Check:**
```css
✓ flex-wrap: wrap; on container?
✓ flex-basis set appropriately?
✓ Container has limited width?
```

### Issue: Unequal Sizing
**Check:**
```css
✓ flex-grow values different?
✓ flex-basis values consistent?
✓ min-width/max-width limiting?
```

### Issue: Overflow on Mobile
**Check:**
```css
✓ No horizontal scroll?
✓ flex-wrap: wrap; active?
✓ 100% width items at breakpoint?
✓ padding/margin not excessive?
```

---

## Browser DevTools Tips

### View Flex Info
1. Right-click element → Inspect
2. Look for "flex" badge in Elements panel
3. Click badge to show flex lines

### Edit Flex Properties
1. In Styles panel, find flex properties
2. Click values to edit live
3. See changes in real-time

### Test Responsive
1. Click device toggle (phone icon)
2. Select preset devices
3. Observe flex layout changes

---

## Reference Table

| Property | Values | Default | Use |
|----------|--------|---------|-----|
| `display` | flex, grid | block | Enable flexbox |
| `flex-direction` | row, column, etc | row | Main axis |
| `justify-content` | flex-start, center, space-between, etc | flex-start | Main axis align |
| `align-items` | flex-start, center, stretch, etc | stretch | Cross axis align |
| `flex-wrap` | nowrap, wrap | nowrap | Line wrapping |
| `gap` | px, rem, % | 0 | Item spacing |
| `flex-basis` | px, %, auto | auto | Item size |
| `flex-grow` | number | 0 | Growth factor |
| `flex-shrink` | number | 1 | Shrink factor |
| `flex` | shorthand | 0 1 auto | Growth/shrink/basis |
| `order` | number | 0 | Visual order |
| `align-self` | flex-start, center, etc | auto | Single item align |

---

## Key Takeaways

✨ **Flexbox is powerful for:**
- One-dimensional layouts (rows or columns)
- Responsive grids with wrapping
- Perfect centering (both axes)
- Equal-height columns
- Space distribution

✨ **Best Practices:**
- Use `gap` instead of margins
- Combine `flex-basis` with `@media` for responsive
- Always include `flex-wrap: wrap;` for mobile
- Use `min-width` to prevent over-shrinking
- Comment complex flex calculations

✨ **This Project Demonstrates:**
- [x] All major flex properties
- [x] Responsive grid layout
- [x] Mobile-first approach
- [x] Complex nested flex containers
- [x] Common flex patterns
- [x] Hover and transition effects

---

*Reference Card for Responsive Flexbox Layout - Task 3*
*Last Updated: January 2026*
