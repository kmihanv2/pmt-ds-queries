SELECT
  date,
  CASE
    WHEN region_level_2 = 'NORAM' THEN 'NA'
  ELSE
  region_level_2
END
  AS region,
  CASE
    WHEN accounts = 'Total GMV' THEN 'GMV'
    WHEN accounts = 'Total GPV (Roll Up)' THEN 'GPV'
    WHEN accounts = 'GPV Penetration Rate (Roll Up)' THEN 'GPV_Pen'
  ELSE
  accounts
END
  AS accounts,
  merchant_type,
  SUM(current_year_investment_plan) AS IP,
  SUM(current_quarterly_forecast) AS LE,
  SUM(actuals) AS Actuals_Check,
FROM
  `shopify-finance-tech-accel.adaptive.adaptive_unified_table`
WHERE
  (accounts = 'Total GMV'
    OR accounts = 'Total GPV (Roll Up)'
    OR accounts = 'GPV Penetration Rate (Roll Up)')
  AND date >= '2023-01-01'
  AND Current_Year_Investment_Plan > 0.0
  AND region_level_2 IS NOT NULL
GROUP BY
  1,
  2,
  3,
  4
ORDER BY
  1
