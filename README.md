# 🧠 LLM Reasoners for Financial Statement Analysis

**Author:** Xiaoxu (Susie) Li  

**Degree:** MSc in Computer Science, The University of Hong Kong  

**Supervisor:** Prof. Lingpeng Kong 

**Date:** May 2025  

**Repository:** [COMP7704_dissertation](https://github.com/lxx-holmes/COMP7704_dissertation)

---

## 📘 Overview

This dissertation introduces **Value Investing Agents (VIA)** — a **multi-agent, multimodal LLM framework** designed to perform *Buffett-style* financial statement analysis and value investing.  
The system simulates a team of specialized AI analysts who collectively analyze company fundamentals, generate insights, and backtest long-term investment strategies.

> Traditional value investing requires deep reasoning across large volumes of data and qualitative reports.  
> VIA automates this process using **agentic collaboration**, **self-critique loops**, and **cross-source verification**, achieving higher analytical accuracy and depth compared to baselines like *Manus* and *OpenAI Deep Research*.

---

## 🧩 Framework Architecture

VIA is composed of four coordinated AI teams:

<p align="center">
  <img src="figures/VIA framework.png" width="1000" alt="Figure 3 – VIA Framework Architecture"><br>
  <em>Overall VIA architecture</em>
</p>


1. **Data Specialists Team** – Extracts and verifies 10-K filings and market data using multimodal models.  

<p align="center">
  <img src="figures/page15_img1.png" width="1000" alt="Figure 4 – Data verification pipeline">
  <em>Data verification pipeline</em>
</p>

2. **Industry Research Team** – Summarizes sector benchmarks and competitive positioning.  
  
Samples of the industry expert’s output on industrial insights

| Sector | Subsector | Metrics |
|:--------|:-----------|:---------|
| **Technology** | Consumer Electronics | "Unit sales growth", "ASP trends", "Product lifecycle metrics", "Margin by product line", "Innovation pipeline value" |
| **Energy** | Oil & Gas Integrated | "Reserve replacement ratio", "Production growth", "Refining margins", "Break-even oil price", "Carbon intensity metrics" |
  

3. **Analyst Team** – Junior and senior analysts collaborate to analyze company fundamentals over multiple years using five dimensions:
   - Business Strategy  
   - Income Statement Quality  
   - Balance Sheet Quality  
   - Cash Flow Quality  
   - Ratio Analysis  
   *(Figures 5–12: Analytical frameworks and workflows)*

4. **Valuation & Trading Team** – Performs intrinsic valuation (P/E, EV/EBITDA, P/S) and trading backtests.

   <div style="max-width: 920px; margin: 24px auto; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif; line-height: 1.55;">
  <div style="border: 1px solid #d0d7de; border-radius: 10px; box-shadow: 0 4px 14px rgba(27,31,36,0.06); overflow: hidden;">
    
    <!-- Header -->
    <div style="background: #0b5fff; color: #fff; padding: 16px 20px;">
      <h2 style="margin: 0; font-size: 20px;">Valuation Report — AAPL</h2>
      <div style="opacity: 0.95; font-size: 14px;">2023-11-03 (FY2023 Q4 Results)</div>
    </div>

    <!-- Key Values -->
    <div style="padding: 18px 20px 6px; display: grid; grid-template-columns: repeat(3, minmax(0,1fr)); gap: 12px;">
      <div style="background:#f6f8fa; border:1px solid #eaeef2; border-radius:8px; padding:12px;">
        <div style="font-size:12px; color:#57606a; text-transform:uppercase; letter-spacing:.04em;">Intrinsic Value / Share</div>
        <div style="font-weight:700; font-size:18px; color:#0b5fff;">$160</div>
      </div>
      <div style="background:#f6f8fa; border:1px solid #eaeef2; border-radius:8px; padding:12px;">
        <div style="font-size:12px; color:#57606a; text-transform:uppercase; letter-spacing:.04em;">Safety Margin</div>
        <div style="font-weight:700; font-size:18px;">15%</div>
      </div>
      <div style="background:#f6f8fa; border:1px solid #eaeef2; border-radius:8px; padding:12px;">
        <div style="font-size:12px; color:#57606a; text-transform:uppercase; letter-spacing:.04em;">Upper Bound</div>
        <div style="font-weight:700; font-size:18px;">30%</div>
      </div>
    </div>

    <!-- Body -->
    <div style="padding: 8px 20px 18px;">
      <h3 style="margin:14px 0 6px; font-size:16px;">Valuation Analysis</h3>
      <p style="margin: 8px 0;">
        Apple’s stock continued to climb in 2023, reaching about $175/share in early November despite FY2023 seeing a small revenue and profit dip
        (the first annual sales decline since 2019). This pushed Apple’s trailing P/E to roughly 27–28×. Investors treated Apple as a safe haven
        tech stock – it traded at a 35% P/E premium over the S&amp;P 500 and ~22% over median tech peers by late 2023. The valuation implied confidence
        that Apple’s ecosystem momentum would offset the temporary hardware slump.
      </p>
      <p style="margin: 8px 0;">
        Our intrinsic valuation balances Apple’s strong moat with the reality of flat-to-declining FY2023 earnings:
      </p>

      <ul style="margin: 8px 0 10px 20px;">
        <li style="margin:6px 0;">
          <strong>P/E:</strong> We apply <strong>25×</strong> to FY2023 EPS (<strong>$6.15</strong>), a slight contraction from the market’s 27–28×,
          to reflect the growth slowdown. This gives an intrinsic value of roughly <strong>$155</strong> per share. The 25× multiple is still above the
          market’s long-term average, but reasonable given Apple’s superior ROIC (~39% vs ~14% sector) and anticipation of new product cycles
          (e.g., Vision Pro AR headset).
        </li>
        <li style="margin:6px 0;">
          <strong>EV/EBITDA:</strong> Apple’s EV/EBITDA around this time was in the low-20s. We choose ~<strong>18×</strong> for intrinsic value,
          yielding a similar <strong>$150–$160</strong> range. Apple’s EV/EBITDA was ~12% below Microsoft’s in 2023 (AAPL ~19× vs MSFT ~22×) but well above
          Meta’s ~12×, reflecting Apple’s steadier profile.
        </li>
        <li style="margin:6px 0;">
          <strong>P/S:</strong> Around <strong>7× sales</strong> (with ~$383B revenue), Apple’s P/S sat between hardware and software norms. Given stable
          margins, this again points to a value in the mid-$150s (since 5× would be too low and 10× too high for Apple’s mix).
        </li>
      </ul>

      <p style="margin: 8px 0;">
        <strong>DDM Check:</strong> Dividend ~$0.95 (yield 0.55%). Even with an optimistic growth outlook, the DDM value ($45–$50) is only a fraction of the
        stock price – a reminder that investors in 2023 focused on total cash return (dividends + large buybacks) and future growth, not just dividends.
        Apple returned roughly ~$90B via buybacks in FY2023, shrinking share count ~4% and buoying EPS despite flat net income.
      </p>

      <p style="margin: 8px 0;">
        <strong>Conclusion:</strong> Our intrinsic value estimate for late 2023 is about <strong>$160/share</strong>. With the stock at $175+, it appeared
        somewhat overvalued (~10% above intrinsic). The market’s optimism (Apple +28% YTD vs +18% Nasdaq by Nov 2023) was “pricing in” perfect execution
        of Apple’s next moves (continued services growth and a successful Vision Pro launch). Any hiccup would leave market price above intrinsic value.
      </p>

      <!-- Figure caption -->
      <div style="text-align:center; margin-top: 12px; color:#57606a; font-size: 13px;">
        <em>A sample valuation report of AAPL after Nov 2023’s annual report release.</em>
      </div>
    </div>

  </div>
</div>

   *(Figures 17-1 & 17-2: Example valuation reports for Apple Inc.)*

---

## ⚙️ Methodology

### Agent Collaboration
Agents communicate through **natural language reasoning** and use structured **tool calls** for:
- Web and API searches for live financial data  
- OCR and vision models for parsing tables and charts  
- Quantitative analysis for financial ratios and valuation  

### Self-Critique and Refinement
Each report undergoes iterative **LLM self-review** for:
- **Quantitative accuracy** (data consistency)  
- **Qualitative coherence** (reasoning and narrative flow)  

*(Figures 14-1, 14-2: Example of self-refinement process)*

### Models Used
- **Doubao-Vision-Pro-32k** — multimodal data extraction  
- **DeepSeek-R1** — reasoning and self-critique  
- **ChatGPT-4o** — cross-domain industry insights  
- **Tavily Search Agent** — real-time data retrieval

---

## 📊 Dataset

- 100 U.S. listed companies across **11 industries**  
- 10 years of 10-K filings per company  
- Average token length per document: ~123k  
- Enables long-context reasoning and document understanding research  

*(Figures 1 & 2: Industry coverage and token distribution)*

---

## 🔍 Evaluation

### Baseline Comparisons
| Model | Strengths | Weaknesses |
|--------|------------|------------|
| **Manus** | Structured summaries | Shallow reasoning depth |
| **OpenAI Deep Research** | Strong narrative | Low factual consistency |
| **VIA** | Accurate, coherent, verifiable | Higher compute cost |

*(Figures 18–22: Side-by-side comparison with baseline systems)*

### Trading Performance
- Initial capital: \$1,000,000  
- Duration: 2020–2025  
- Outperformed Buy-and-Hold, MACD, and Mean-Reversion strategies  
- Generated **positive alpha** with realistic risk-adjusted returns  

*(Figures 20–22: Portfolio backtest and P&L visualization)*

---

## 🧠 Key Innovations

| Challenge | VIA Solution |
|------------|--------------|
| Long-context document analysis | Recursive extraction and summarization |
| Analytical reasoning | Chain-of-thought with reinforcement refinement |
| Multimodal data fusion | Vision + text table parsing |
| Benchmarking | 10-year backtest and valuation comparison |
| Transparency | Traceable citation of 10-K source data |

---

## 🚀 Future Work

- Expand to real-time portfolio management and dynamic market data streams  
- Implement long-term **LLM memory persistence**  
- Extend dataset to global markets (EU, HK, CN)  
- Integrate hybrid **LLM + quantitative models** for alpha generation  

---

## 📎 Appendix

- **Appendix I:** Prompt engineering templates  
- **Appendix II:** Self-critique examples *(Figures 15–16)*  
- **Appendix III:** Sample input and output data  
- **Appendix IV:** Generated analysis reports  
- **Appendix V:** Dataset and system access links  

---

## 🖼️ Figure Reference Summary

| Section | Figure(s) | Description |
|----------|------------|-------------|
| Dataset | **Fig. 1–2** | Industry coverage and token length distribution |
| Framework | **Fig. 3–4** | VIA architecture and data pipeline |
| Analyst Team | **Fig. 5–12** | Analytical framework and modules |
| Self-Critique | **Fig. 14–16** | LLM refinement process |
| Valuation | **Fig. 17–1, 17–2** | AAPL valuation example |
| Baseline Comparison | **Fig. 18–22** | VIA vs baseline results |

---

## 📚 Citation

If you use or reference this work:

```bibtex
@mastersthesis{li2025LLMReasoners,
  author    = {Li, Xiaoxu (Susie)},
  title     = {LLM Reasoners for Financial Statement Analysis},
  school    = {The University of Hong Kong},
  year      = {2025},
  advisor   = {Prof. Lingpeng Kong}
}
