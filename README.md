# FB
CrypTool Fee Analyzer

Explanations & UI Features
This tool analyzes transaction fees and overpayments in Bitcoin blocks. Coinbase transactions are excluded from user-focused statistics.

Key UI Features Implemented:

Responsive Design: Adapts to various screen sizes, with horizontal scrolling for the main data table on smaller screens to ensure readability.
Collapsible Controls: The main filter controls can be hidden/shown.
Theme Toggle: Switch between light and dark themes.
Layout Order: Choose to display the data table or charts first.
Loading Indicator: Visual feedback during data fetching.
Overpayment vs Min Inclusion Fee: Metric showing "waste" compared to the minimum fee rate required for block inclusion.
Customizable Overpayment Factor: Define overpayment relative to the block's average fee rate.
Interactive Block Detail Analysis: Click a table row or a bar in the "Fee Rates" chart for a detailed block breakdown (fee rate histogram, fee vs. weight scatter plot). Charts in the detail view are highlighted when active.
App Tour: A guided tour (click "App Tour") highlighting key functionalities, with keyboard navigation and auto-advance option.
Date Note: 'Analysis Date' is from the newest block in the set (UTC). Timestamps are UTC.

Interpreting Chart Y-Axis Scales
Linear Scale: Shows absolute differences.
Logarithmic Scale: Shows relative changes, useful for wide fee ranges.

Blk(H): Block height.
Time(UTC): Block mined time.
Blk W(WU): Block weight.
Txs: Total transactions.
Min/Avg/Max Fee: User transaction fees (sat). Formula: min/avg/max(tx.fee).
Min/Avg/Max W: User transaction weights (WU). Formula: min/avg/max(tx.weight).
Min FR: Min user tx fee rate (s/vB). Calc: min(tx.fee / (tx.weight/4)).
Avg FR: Avg user tx fee rate (s/vB). Calc: avg(tx.fee / (tx.weight/4)).
OvAvg%: % user txs with FR(s/WU) > (Custom Factor * block avg user FR(s/WU)). Formula: (count(txs where fr_swu > Factor * block_avg_fr_swu) / count(user_txs)) * 100.
Wasted Sats (vs Avg): Sats 'wasted' by txs with FR(s/WU) > (Custom Factor * block avg user FR(s/WU)). Formula: sum(max(0, tx.fee - (Factor * block_avg_fr_swu * tx.weight))) for relevant txs.
Wasted Fee % (vs Avg): Percentage of total user fees 'wasted' (vs Custom Factor * Avg FR). Formula: (Block_Wasted_Sats_vs_Avg / Total_User_Fees_In_Block) * 100.
Wasted Sats (vs Min Incl): Sats 'wasted' by user txs compared to the minimum fee rate (s/WU) required for inclusion in that specific block. Formula: sum(max(0, tx.fee - (block_min_inclusion_fr_swu * tx.weight))).
>5xMin% / >10xMin%: % user txs with FR(s/WU) > 5x (or 10x) the block's minimum user FR(s/WU). Formula: (count(txs where fr_swu > N * block_min_fr_swu) / count(user_txs)) * 100.
Notes: User Txs = All except Coinbase. s/WU = sats per Weight Unit.
>
