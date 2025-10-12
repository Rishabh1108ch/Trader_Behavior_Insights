---

## 📊 Exploratory Data Analysis (EDA)

### 1️⃣ Distribution of Closed PnL
The distribution of Closed PnL highlights how profitability is spread across all trades.  
Most trades yield modest profits or losses, while a few large outliers significantly influence the total PnL.  
This skewed distribution indicates that a small number of trades or traders contribute disproportionately to overall returns.

---

### 2️⃣ Daily PnL Trend
The daily PnL curve provides insights into trading performance over time.  
Peaks in profitability often align with positive sentiment periods, while dips coincide with market uncertainty.  
This temporal analysis helps in identifying behavioral patterns such as overtrading during volatile phases or reduced activity in fearful markets.

---

### 3️⃣ Market Sentiment vs PnL
By mapping the Fear & Greed Index against trader profitability, we observe a measurable correlation between market sentiment and trading outcomes.  
Higher greed levels sometimes correspond to aggressive risk-taking and short-term profits but also to increased volatility and losses when markets reverse.  
Conversely, during fearful conditions, traders tend to reduce exposure, leading to smaller but more stable PnL results.

---

### 4️⃣ Top Performing Traders
An analysis of cumulative PnL by account reveals that a small group of traders consistently outperform others.  
This suggests strong differences in strategy, experience, or risk management discipline.  
These traders demonstrate consistent returns even under varying sentiment conditions, highlighting the value of emotional control in trading behavior.

---

## 🧮 Regression Analysis — Sentiment Impact on Profitability
A linear regression model was applied to quantify how sentiment (Fear & Greed Index) influences trader profitability.  
The model showed a **moderate positive correlation**, meaning that increases in market greed tend to raise average PnL values, although the effect size is limited.  
This indicates sentiment plays a role in profitability, but other variables (such as timing, volatility, or liquidity) also contribute significantly.

---

## 💡 Key Insights

- Market sentiment has a measurable yet moderate influence on trading results.  
- Overconfidence during “Greed” phases often leads to higher volatility and drawdowns.  
- Most traders’ PnL outcomes are **skewed**, with a few highly profitable traders dominating returns.  
- Incorporating behavioral indicators such as sentiment can improve portfolio risk management.  
- Emotional awareness and disciplined execution outperform impulsive, sentiment-driven decisions.

---

## 📑 Summary of Results

| Aspect | Observation |
|---------|--------------|
| Sentiment–PnL Correlation | Moderate, positive trend |
| Top Trader Performance | Concentrated among a few accounts |
| PnL Distribution | Right-skewed, heavy tail on profitable side |
| Regression R² | Approximately 0.25 — partial linear relationship |
| Behavioral Insight | Traders take riskier positions during “Greed” phases |

---

## 🧭 Conclusion
This analysis demonstrates that **market sentiment significantly shapes trader behavior** in the cryptocurrency market.  
While greed can drive short-term gains, it also amplifies risk exposure and loss potential.  
Effective traders balance sentiment awareness with data-driven strategy, achieving consistency through discipline rather than emotion.  
These insights can guide the development of **behavioral trading models**, **risk controls**, and **sentiment-aware dashboards**.

---

## 🚀 Future Work

- Integrate additional features such as market volatility, token volume, and open interest.  
- Expand the regression model to non-linear or ensemble methods like **Random Forest** or **XGBoost**.  
- Build a **Power BI or Plotly dashboard** for real-time sentiment monitoring.  
- Analyze individual trader psychology through session-level metrics and behavioral clustering.

---

## 👨‍💻 Author
**Rishabh Chandrakar**  
*Data Analyst | Supply Chain & Trading Analytics Enthusiast*  
📧 rishabhchandrakar684@gmail.com  
💼 [LinkedIn](https://linkedin.com/in/rishabhchandrakar)

---
