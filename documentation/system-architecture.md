AI Stock Hunter — System Architecture
1. Project Overview
AI Stock Hunter is a stock analysis and alert system designed to collect market data, calculate technical indicators, evaluate trading conditions, and deliver understandable analysis reports.
The initial development focuses on NVIDIA (NVDA).
The project follows an n8n-first architecture to minimize coding requirements and keep initial development costs as low as possible.
2. System Architecture
The planned system consists of the following components:
1. User Interface  
    * LINE Messaging API (planned for Phase 4).
    * Users can request stock analysis and receive alerts.
2. Workflow Engine  
    * n8n manages automation and workflow execution.
    * Scheduled Trigger runs periodic stock scans.
    * Webhook receives requests from external services.
3. Market Data Provider  
    * Retrieves stock prices, historical data, and trading volume.
    * Initial target: NVDA.
    * Data providers must be evaluated for reliability, API limits, and free-tier availability.
4. Data Processing  
    * Validates incoming market data.
    * Normalizes timestamps and price formats.
    * Handles missing or incomplete data.
5. Technical Analysis  
    * RSI
    * MACD
    * Trading Volume
    * Support and Resistance
    * Breakout and Breakdown detection
6. Analysis Engine  
    * Rule-based logic evaluates technical conditions.
    * AI Analyst may explain signals and summarize risks.
    * AI must use actual market data and must not invent missing values.
7. Notification System  
    * Generates analysis reports.
    * Sends alerts through LINE when implemented.
    * Supports price and technical-indicator alerts.
3. Workflow Diagram
             USER
               |
               v
        LINE Messaging API
          (Future Phase)
               |
               v
         n8n Webhook
               |
               v
        Market Data API
               |
               v
      Data Validation
      and Normalization
               |
               v
      Technical Indicators
       RSI / MACD / Volume
               |
               v
        Analysis Engine
         /          \
        v            v
  Rule-based      AI Analyst
   Analysis       (Optional)
        \            /
         v          v
        Analysis Report
               |
               v
        LINE Notification
          (Future Phase)
Scheduled Scan Workflow
A separate scheduled workflow will periodically:
1. Retrieve the latest market data.
2. Validate and process the data.
3. Calculate technical indicators.
4. Evaluate predefined trading conditions.
5. Generate a report.
6. Send an alert when configured conditions are met.
4. Development Principles
* Prefer free and open-source tools whenever practical.
* Use n8n as the primary automation platform.
* Keep Python as an optional future extension.
* Start with NVDA before expanding to additional stocks.
* Separate calculations from AI-generated explanations.
* Never treat an AI-generated prediction as a guaranteed outcome.
* Do not execute real-money trades automatically.
5. Data and Security
* API credentials and secret keys must be stored securely in n8n credentials.
* Never commit API keys, passwords, or private tokens to GitHub.
* Respect API rate limits and provider terms.
* Record timestamps and use consistent timezone handling.
* Identify missing, delayed, or unreliable market data.
* Maintain workflow logs for troubleshooting.
6. Testing and Risk Management
Before using the system for real investment decisions:
* Test indicator calculations.
* Perform historical backtesting.
* Evaluate Win Rate and Maximum Drawdown.
* Run paper trading.
* Monitor false signals and data reliability.
The system is an analytical tool, not a guarantee of investment returns.
7. Planned Development Phases
Phase	Main Objective
Phase 1	n8n and GitHub foundations
Phase 2	Market data and technical indicators
Phase 3	AI Analyst and risk evaluation
Phase 4	LINE Bot integration
Phase 5	Alerts, backtesting, and paper trading
Phase 6	Deployment, security, and stability
Refer to roadmap.md for the detailed development schedule.
8. Current Development Status
The project is currently in Phase 1.
Initial development is being performed using an iPad Gen 9 and a web browser. Actual n8n deployment and execution will be addressed when a suitable environment is available.
