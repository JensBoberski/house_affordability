# Affordability Map

A single-file interactive tool for calculating Israeli real estate affordability.

## What it is

A standalone HTML page (no build step, no dependencies to install) that helps buyers understand their purchase ceiling given:
- Available capital (down payment + closing costs)
- Maximum monthly mortgage payment
- Mortgage rate and term

## How it works

Three constraints intersect to define the affordable range:
1. **Capital constraint** — how much loan capital allows (rises with price as closing costs grow)
2. **Monthly constraint** — max loan size your monthly budget can service (flat line)
3. **Legal floor** — Israeli law requires minimum 25% down payment (slopes up with price)

The ceiling is the price where no loan simultaneously satisfies all three.

## Key outputs

- **Max affordable price** — exact ceiling (interpolated)
- **Affordability table** — mortgage × price grid, colour-coded green/blue/red/striped
- **Affordability chart** — visual intersection of all three constraints
- **Closing cost breakdown** — purchase tax (מס רכישה), lawyer, agent, broker, appraiser

## Israeli tax brackets (מס רכישה)

| Up to | Rate |
|---|---|
| ₪1,978,745 | 0% |
| ₪2,347,040 | 3.5% |
| ₪3,054,195 | 5% |
| ₪5,872,725 | 8% |
| Above | 10% |

These are the 2024 brackets for first-home buyers (zero tax on first ~₪2M).
Update the `TAX_BRACKETS` array in `index.html` if the government changes them.

## Tech stack

| Layer | Choice |
|---|---|
| UI framework | React 18 (CDN) |
| Charts | Recharts 2.9 (CDN) |
| JSX transform | Babel Standalone (CDN) |
| Fonts | DM Sans + DM Mono (Google Fonts) |
| Build | None — single `index.html` |

## Deployment (GitHub Pages)

1. Push `index.html` to a repo
2. Go to **Settings → Pages → Source: main / root**
3. Live at `https://<username>.github.io/<repo>/`

## File structure

```
affordability-map/
└── index.html    # entire app — HTML + CSS + JSX in one file
└── CLAUDE.md     # this file
```

## Editing

Everything lives in `index.html`. Key sections (search by comment):

| Comment | What's there |
|---|---|
| `─── TAX` | Purchase tax brackets + closing cost calc |
| `─── THEMES` | Light / dark colour tokens |
| `─── SLIDER` | Reusable slider component |
| `─── TOOLTIP` | Chart hover tooltip |
| `─── TABLE` | Affordability grid table |
| `─── MAIN` | App state, chart data, layout |
