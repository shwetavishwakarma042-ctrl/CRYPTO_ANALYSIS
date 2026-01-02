This file includes all the measures and DAX expressions used during the project.

## MOMENTUM RATING

```dax
MOMENTUM RATING =
VAR M = [GROWTH MOMENTUM]
RETURN
SWITCH(
    TRUE(),
    ISBLANK(M), "NO DATA",
    M >= 0.50, "STRONG UPTREND",
    M >= 0.20, "MODERATE UPTREND",
    M >= 0.00, "SIDEWAYS/STABLE",
    M >= -0.20, "WEAK DOWNTREND",
    "STRONG DOWNTREND/REVERSAL RISK"
)
```

## MOMENTUM SCORE

```dax
MOMENTUM SCORE =
VAR M = [GROWTH MOMENTUM]
RETURN
SWITCH(
    TRUE(),
    ISBLANK(M), BLANK(),
    M >= 0.50, 100,
    M >= 0.20, 80,
    M >= 0.00, 60,
    M >= -0.20, 40,
    M >= -0.50, 20,
    10
)
```

## PAST PRICE 7D

```dax
PAST PRICE 7D =
VAR CURRENTPRICE = SELECTEDVALUE(CRYPTO[current_price])
VAR CHANGE7D = SELECTEDVALUE(CRYPTO[PRICE_CHANGE_PERCENTAGE_7D_IN_CURRENCY], 0)
RETURN
DIVIDE(CURRENTPRICE, (1 + CHANGE7D / 100))
```

## GROWTH SCORE

```dax
GROWTH SCORE =
VAR G = SELECTEDVALUE(CRYPTO[price_change_percentage_7d_in_currency], 0)
RETURN
SWITCH(
    TRUE(),
    ISBLANK(G), 0,
    G >= 30, 20,
    G >= 15, 15,
    G >= 5, 10,
    G >= 0, 5,
    G <= 0, 1
)
```

## GROWTH MOMENTUM

```dax
GROWTH MOMENTUM =
VAR WEEKLY = SELECTEDVALUE(CRYPTO[price_change_percentage_7d_in_currency])
VAR DAILY = SELECTEDVALUE(CRYPTO[price_change_percentage_24h_in_currency])
RETURN
IF(
    ISBLANK(WEEKLY) || ISBLANK(DAILY),
    BLANK(),
    DIVIDE(WEEKLY - DAILY, ABS(DAILY))
)
```

