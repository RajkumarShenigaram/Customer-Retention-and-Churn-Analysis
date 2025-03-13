		WITH users_signup_month AS (
			-- Step 1: Get each user's first sale date and signup month
			SELECT 
				user_id, 
				MIN(sale_date) AS first_sale_date,
				DATE_TRUNC('month', MIN(sale_date)) AS signup_month
			FROM sales_data
			GROUP BY user_id
		),

		ranked_sales AS (
			-- Step 2: Rank products by highest spend in the first month
			SELECT 
				s.user_id, 
				s.product_name AS signup_product, 
				s.sales_amount,
				ROW_NUMBER() OVER (PARTITION BY s.user_id ORDER BY s.sales_amount DESC) AS rank
			FROM sales_data s
			JOIN users_signup_month u 
				ON s.user_id = u.user_id 
				AND DATE_TRUNC('month', s.sale_date) = u.signup_month
		),

		signup_product_cte AS (
			-- Step 3: Select the highest spend product for each user
			SELECT user_id, signup_product
			FROM ranked_sales
			WHERE rank = 1
		),

		month_start_dates AS (
			-- Step 4: Generate a series of month start dates for cross-joining
			SELECT DATE_TRUNC('month', generate_series('2025-01-01'::date, '2025-06-01'::date, interval '1 month')) AS month_start_date
		),

		user_month_cross_join AS (
			-- Step 5: Cross join users with month start dates
			SELECT 
				u.user_id, 
				m.month_start_date, 
				u.signup_month
			FROM users_signup_month u
			CROSS JOIN month_start_dates m
			WHERE m.month_start_date >= u.signup_month  -- Ensure months are after signup
		),

		monthly_spend_cte AS (
			-- Step 6: Aggregate monthly spend per user
			SELECT 
				user_id, 
				DATE_TRUNC('month', sale_date) AS month_start_date, 
				SUM(sales_amount) AS month_spend
			FROM sales_data
			GROUP BY user_id, DATE_TRUNC('month', sale_date)
		),

		final_table AS (
			-- Step 7: Join all tables to get the final output
			SELECT 
				um.user_id, 
				um.month_start_date, 
				um.signup_month,
				DATE_DIFF('month', um.signup_month, um.month_start_date) AS nth_month, -- Calculate nth month
				sp.signup_product, 
				COALESCE(ms.month_spend, 0) AS month_spend
			FROM user_month_cross_join um
			LEFT JOIN monthly_spend_cte ms 
				ON um.user_id = ms.user_id 
				AND um.month_start_date = ms.month_start_date
			LEFT JOIN signup_product_cte sp
				ON um.user_id = sp.user_id
		)

		SELECT * FROM final_table;
