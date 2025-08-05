# Bitcoin Lottery Mining vs. Powerball Calculator

## Overview
The **Bitcoin Lottery Mining vs. Powerball Calculator** is a web-based tool that compares the odds and rewards of Bitcoin mining (Solo Mining or Parasite Pool) with playing the Powerball lottery. It calculates the **annual odds** of winning a significant reward, **odds per try** (per Bitcoin block or Powerball ticket), and the **reward at stake** for each model, helping users understand the probabilistic trade-offs between mining and Powerball. The calculator is designed to be user-friendly, with a clean interface and flexible hash rate inputs.

## Features
- **Mining Models**:
  - **Solo Mining**: Calculates odds based on your individual hash rate against the Bitcoin network.
  - **Parasite Pool**: Reflects the pool’s hybrid model (1 BTC to the block finder, ~2.125 BTC distributed proportionally, zero fees).
- **Powerball Comparison**: Compares mining odds and rewards to Powerball’s jackpot ($500M) and ticket cost ($312/year, based on $2/ticket × 156 draws).
- **Dual Hash Rate Inputs**: Users input hash rates with a number and unit dropdown (KH/s to EH/s) for Your Hash Rate, Bitcoin Network Hash Rate, and Parasite Pool Hash Rate.
- **Output**:
  - **Main Table**: Shows annual odds and reward at stake for the selected model vs. Powerball.
  - **Per-Try Table**: Shows odds per try (per block or ticket) and reward at stake.
  - **Odds Comparison**: Narrative explaining which model has better odds, Powerball’s larger jackpot, and mining’s frequent attempts (52,500 blocks/year vs. 156 draws).
  - **Math Explanation**: Details the annual odds calculation (1 - (1 - per-try odds)^events).
- **Responsive Design**: Two-column hash rate inputs (number and unit) in one row, consistent across desktop and mobile.

## Prerequisites
- A modern web browser (e.g., Chrome, Firefox, Safari).
- No external dependencies; the calculator is a standalone HTML file with embedded CSS and JavaScript.

## Installation
1. Download the `index.html` file from the repository.
2. Save it to your local machine or a server.
3. No additional setup is required, as the file is self-contained.

## Usage
1. **Open the Calculator**:
   - Open `index.html` in a browser using `file://` (local) or host it on a server (e.g., `python -m http.server` for local testing).
2. **Select a Mining Model**:
   - Choose **Solo Mining** or **Parasite Pool** from the dropdown.
3. **Enter Inputs**:
   - **Your Hash Rate**: Default 1 TH/s (value: 1, unit: TH/s).
   - **Bitcoin Network Hash Rate**: Default 944 EH/s (value: 944, unit: EH/s).
   - **Parasite Pool Hash Rate**: Default 10 PH/s (value: 10, unit: PH/s, adjustable for future changes).
   - **Bitcoin Block Reward**: Default 3.125 BTC.
   - **Bitcoin Price**: Default $114,000.
   - **Electricity Cost per Year**: Default $40.
   - **Hardware Cost per Year**: Default $200.
4. **Calculate**:
   - Click the **Calculate Odds** button to view results.
5. **View Results**:
   - **Main Table**: Annual odds (1 in X) and reward at stake for each model vs Powerball.
   - **Per-Try Table**: Odds per try (per block or ticket) and reward at stake.
   - **Model-Specific Breakdown**: Detailed explanation of rewards and Powerball comparisons.
   - **Odds Comparison**: Explains which model has better odds vs Powerball.
   - **Math Explanation**: Describes the formula for annual odds.

### Example Output (Defaults)
**Parasite Pool**:
```
Comparison: Parasite Pool vs. Powerball
| Model         | Annual Odds    | Reward at Stake   |
|---------------|----------------|-------------------|
| Parasite Pool | 1 in 73,300    | $114,000          |
| Powerball     | 1 in 1,873,077 | $500,000,000      |
Odds per Try
| Model         | Odds per Try      | Reward at Stake   |
|---------------|-------------------|-------------------|
| Parasite Pool | 1 in 73,300       | $114,000          |
| Powerball     | 1 in 292,200,000  | $500,000,000      |
Odds Comparison: Parasite Pool has better annual odds (1 in 73,300) than Powerball (1 in 1,873,077) for winning any reward (1 BTC or proportional). However, Powerball's massive $500,000,000 jackpot dwarfs Parasite Pool's $114,000 for the big win in Parasite Pool (plus proportional rewards) or full block reward in Solo Mining. Parasite Pool's 1 blocks/year boost engagement with 52,500 annual attempts compared to Powerball's 156 draws.
Annual Odds Calculation: The annual odds represent the probability of winning a reward in a year. For Solo Mining, this is the probability of winning the full block reward, calculated as 1 minus the probability of not winning any of the 52,500 blocks: 1 - (1 - per-block odds)^52,500, where per-block odds are your hash rate divided by the network hash rate (e.g., 1 TH/s ÷ 944 EH/s). For Parasite Pool, annual odds reflect the pool’s probability of winning any reward (1 BTC or proportional), using the pool’s hash rate divided by the network hash rate (e.g., 10 PH/s ÷ 944 EH/s). For Powerball, annual odds are 1 - (1 - 1/292,200,000)^156, based on 156 draws. Odds per try are per block (Bitcoin) or per ticket (Powerball), with the reward at stake being the potential payout for a win.
```

## Technical Details
- **File**: `index.html` (single HTML file with embedded CSS and JavaScript).
- **HTML Structure**:
  - Input fields for mining model, hash rates, block reward, Bitcoin price, and costs.
  - Two tables for output: main (annual odds, reward) and per-try (odds per try, reward).
  - Narrative and math explanation sections.
- **CSS**:
  - Responsive design with `flex` for two-column hash rate inputs (2:1 ratio).
  - Mobile-friendly layout (adjusts gap, maintains two columns).
  - Clean styling with tables, borders, and blue accents.
- **JavaScript**:
  - Handles input validation (positive numbers, costs can be 0).
  - Calculates odds using `1 - (1 - per-try odds)^events`.
  - Toggles Parasite Pool input visibility based on model selection.
  - Uses `window.calculateOdds` for global access to avoid `ReferenceError`.
- **Math**:
  - **Solo Mining**: Annual odds = 1 - (1 - (hashRate / networkHashRate))^52,500; per-try = hashRate / networkHashRate; reward = 3.125 BTC × $114,000.
  - **Parasite Pool**: Annual odds = 1 - (1 - (parasiteHashRate / networkHashRate))^52,500; per-try = parasiteHashRate / networkHashRate; Big Win = 1 BTC ($114,000), Small Reward = proportional share of 2.125 BTC.
  - **Powerball**: Annual odds = 1 - (1 - 1/292,200,000)^156; per-try = 1/292,200,000; reward = $500M.
- **Defaults**:
  - Your Hash Rate: 1 TH/s.
  - Network Hash Rate: 944 EH/s.
  - Parasite Pool Hash Rate: 10 PH/s.
  - Block Reward: 3.125 BTC.
  - Bitcoin Price: $114,000.
  - Electricity Cost: $40/year.
  - Hardware Cost: $200/year.
  - Powerball: $500M, $312/year.

## Troubleshooting
- **Button Not Working**: Check the browser console (F12) for errors. Ensure no browser extensions (e.g., ad blockers) interfere, though the code is standalone.
- **Incorrect Output**: Verify input values are valid (positive numbers, costs can be 0). Test in a clean browser profile (e.g., Chrome, Firefox).
- **Mobile Display**: Hash rate inputs should remain two columns per row; if not, check CSS media queries or test in another browser.

## Future Enhancements
- Add a Chart.js bar chart to visualize odds comparison.
- Include lifetime odds (e.g., over 50 years with network growth).
- Add a reset button to restore default values.
- Incorporate cost analysis (e.g., luck per dollar) if requested.

## License
This project is open-source and available for personal or educational use. No warranty is provided.

## Contact
For issues or suggestions, please open an issue on the repository or contact the developer.

