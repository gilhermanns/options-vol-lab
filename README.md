# Options Pricing & Volatility Lab

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A comprehensive toolkit for **options pricing, volatility modeling, and calibration**, built from scratch. This project provides a robust framework for understanding and implementing advanced derivatives analytics, crucial for **Private Banking, Wealth Management, and Institutional Trading Desks** involved in structured products, hedging, and risk management.

## Business Relevance

For financial professionals in **Private Banking, Wealth Management, and Institutional Investment**, a deep understanding of options and volatility is essential for:

-   **Structured Products**: Designing and pricing complex derivatives for client portfolios.
-   **Hedging Strategies**: Implementing effective risk mitigation using options to protect portfolios against adverse market movements.
-   **Risk Management**: Quantifying and managing exposure to volatility, a key driver of options prices.
-   **Portfolio Optimization**: Incorporating options into multi-asset portfolios for enhanced returns or reduced risk.
-   **Arbitrage & Trading**: Identifying mispricings and executing sophisticated trading strategies.

This lab demonstrates the underlying mechanics of options valuation and volatility dynamics, providing a solid foundation for practical applications in a professional setting.

## Motivation (Applied Perspective)

This project addresses critical questions faced by derivatives practitioners:

-   Do different pricing models (Black-Scholes, Binomial Tree, Monte Carlo) converge, and what are their strengths and weaknesses in various market conditions?
-   How accurately can implied volatility be extracted from market prices, and how reliable are these measures for future price movements?
-   Can stochastic volatility models (like Heston) effectively capture the observed volatility smile and term structure, and how robust is their calibration?

## Methodology

-   **Pricers (`options_vol_lab.pricers`)**: Implements Black-Scholes (closed-form), Cox-Ross-Rubinstein (binomial tree for European/American options), and Monte Carlo (for GBM with variance reduction) pricers. These are cross-validated to ensure accuracy and consistency.
-   **Greeks (`options_vol_lab.greeks`)**: Provides both analytic (Black-Scholes) and finite-difference implementations for Delta, Gamma, Vega, Theta, and Rho. This allows for cross-checking and understanding the sensitivity of option prices to various parameters.
-   **Implied Volatility (`options_vol_lab.implied_vol`)**: Utilizes Brent's method for robust inversion of Black-Scholes prices to derive implied volatility, with checks for intrinsic value and search bounds.
-   **Heston Model (`options_vol_lab.heston`)**: Features a semi-closed-form pricer (Fourier inversion), an Euler path simulator for Monte Carlo, and a `scipy.optimize.least_squares` calibrator to fit Heston parameters to a target implied-volatility surface. This demonstrates advanced stochastic volatility modeling and calibration techniques.
-   **Surface Construction (`options_vol_lab.surface`)**: Builds synthetic volatility surfaces from simulated Heston paths, providing a controlled environment to test pricing and calibration algorithms.

## Sample Output & Insights

This lab generates detailed outputs and visualizations, crucial for understanding options behavior:

-   **Single-Option Pricing & Greeks**: Demonstrates agreement across different pricing models and validates analytic Greeks against finite differences.
-   **Volatility Surface (Synthetic Heston Market)**: Visualizes the implied volatility smile and term structure, showing how volatility varies by strike and maturity. This is critical for identifying market expectations and potential arbitrage opportunities.
-   **Heston Calibration Round Trip**: Shows the accuracy of parameter recovery after calibrating the Heston model to a synthetic market, validating the robustness of the calibration process.

*(Example charts and tables would be embedded here, showcasing option prices, Greek values, volatility surfaces, and calibration results.)*

## Project Structure

```text
/options-vol-lab
├── README.md               # Project documentation
├── requirements.txt        # Python dependencies
├── main.py                 # Main execution script (if applicable)
├── scripts/                # Utility scripts for running simulations and reports
└── src/
    ├── options_vol_lab/    # Core options pricing and volatility logic
    │   ├── pricers/        # Option pricing models
    │   ├── greeks/         # Greek calculation modules
    │   ├── implied_vol/    # Implied volatility solvers
    │   ├── heston/         # Heston model implementation
    │   └── surface/        # Volatility surface construction
```

## Getting Started

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/gilhermanns/options-vol-lab.git
   cd options-vol-lab
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run examples:
   ```bash
   python scripts/build_surface.py
   ovl-price --spot 100 --strike 105 --rate 0.03 --vol 0.22 --ttm 0.5 --type call
   ```

## License & Disclaimer

This project is licensed under the MIT License. It is intended for educational and research purposes in quantitative finance. The models and results presented are for illustrative purposes and do not constitute financial advice or guarantee real-world performance. Always exercise professional judgment and conduct thorough due diligence when dealing with financial instruments.
