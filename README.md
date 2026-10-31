# Philippines Holiday Pay & Overtime Calculator

A responsive, standalone HTML calculator for estimating **Philippine holiday pay and overtime pay**, using standard Department of Labor and Employment (DOLE) multipliers. No frameworks, dependencies, account, or backend required.

## Features

- Basic daily wage in Philippine pesos (PHP)
- Ordinary working day, regular holiday, and special non-working day
- Scheduled rest-day premiums
- Regular hours and overtime hours
- Optional 10% night shift differential for hours worked from 10 PM to 6 AM, separately for regular and overtime hours
- Automatic breakdown of regular pay, overtime pay, and total estimated gross pay
- Responsive layout, input validation, reset, and print button
- Works offline after downloading `index.html`

## Quick start

1. Download or clone this repository.
2. Open `index.html` in any modern browser.
3. Enter your basic daily wage, choose the day type, and enter hours worked.
4. The results update automatically.

## Publish with GitHub Pages

1. Create a GitHub repository (for example, `ph-holiday-pay-calculator`).
2. Upload `index.html` and `README.md` to the repository root and commit them to the `main` branch.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, then select **main** and **/(root)**. Save.
5. After deployment, your site will usually be available at `https://YOUR-USERNAME.github.io/ph-holiday-pay-calculator/` (replace placeholders with your actual names).

## Formulas

Assuming an 8-hour workday:

```text
Basic hourly rate = Daily basic wage / 8
Regular worked pay = Hourly rate × Regular hours worked × Day multiplier
Overtime pay = Hourly rate × Day multiplier × Overtime factor × Overtime hours
Night differential for regular hours = Hourly rate × Day multiplier × 10% × Eligible night regular hours
Night differential for overtime = Hourly rate × Day multiplier × Overtime factor × 10% × Eligible night overtime hours
Total gross pay = Regular worked pay + Overtime pay + Night differential
```

| Day type | Worked day multiplier | Overtime factor | Effective OT hourly multiplier |
| --- | ---: | ---: | ---: |
| Ordinary day | 1.00× | 1.25× | 1.25× |
| Ordinary rest day | 1.30× | 1.25× | 1.625× |
| Regular holiday | 2.00× | 1.30× | 2.60× |
| Regular holiday + rest day | 2.60× | 1.30× | 3.38× |
| Special non-working day | 1.30× | 1.30× | 1.69× |
| Special non-working day + rest day | 1.50× | 1.30× | 1.95× |

**Non-worked days:** An eligible unworked regular holiday is estimated at 100% of basic daily wage. An unworked special non-working day or ordinary day is estimated at zero under the standard no-work-no-pay assumption. Eligibility and employer policy may change actual pay.

### Example

For a **₱800** basic daily wage, **8 regular hours**, and **2 overtime hours** on a regular holiday (not a rest day):

```text
Hourly rate = ₱800 / 8 = ₱100
Holiday pay = ₱100 × 8 × 2.00 = ₱1,600
Holiday OT = ₱100 × 2.00 × 1.30 × 2 = ₱520
Estimated total = ₱2,120
```

## Limitations and disclaimer

This is an **unofficial educational estimate**, not legal or payroll advice, and is **not affiliated with DOLE**. It calculates night shift differential from the night hours you enter, but does not automatically determine night hours from clock-in/out times, handle cross-midnight holiday changes, overlapping holidays, payroll deductions, or collective bargaining/company-specific premiums. For part-day attendance and eligibility to unworked regular-holiday pay, confirm the proper treatment with your employer or DOLE. Overtime hours should be hours beyond the normal eight-hour workday; regular hours are limited to eight in this calculator.

## Project structure

```text
ph-holiday-pay-calculator/
├── index.html
└── README.md
```

## License

You may add a license file of your choice before publishing or accepting contributions.

### Night shift differential example

For an ordinary working day with ₱600 daily wage, 8 worked hours, no overtime, and all 8 hours eligible for night differential:

```text
Basic hourly rate = ₱600 ÷ 8 = ₱75.00
Night differential per hour = ₱75.00 × 10% = ₱7.50
Night differential for 8 hours = ₱7.50 × 8 = ₱60.00
Total estimated pay = ₱600.00 + ₱60.00 = ₱660.00
```

Check **Include night shift differential** and enter the eligible night regular/overtime hours. Night hours must not exceed the respective hours worked. Only hours actually worked between 10 PM and 6 AM count; subtract unpaid breaks.
