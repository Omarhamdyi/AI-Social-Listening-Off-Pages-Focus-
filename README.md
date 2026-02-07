# AI-Social-Listening-Off-Pages-Focus-

AI Social Listening Solution - Eva Cosmetics Hackathon Challenge CH-05

PROJECT OVERVIEW:
-----------------
End-to-end AI pipeline for off-page social listening with bilingual support
(Arabic + English). Analyzes brand mentions across social media platforms,
classifies sentiment and topics, and generates actionable insights.

SETUP INSTRUCTIONS:
1. REQUIREMENTS:
   - Google Colab (recommended) OR
   - Python 3.8+
   - 12GB RAM minimum
   - Internet connection (first run only, to download models)

2. DEPENDENCIES:
   All dependencies are installed automatically in Cell 1:
   - transformers==4.35.0
   - torch
   - pandas
   - openpyxl
   - scikit-learn
   - tqdm

3. INPUT DATA:
   Place the following file in the same directory as the notebook:
   - eva_social_listening_INPUT_FINAL.csv


HOW TO RUN:

METHOD 1: Google Colab (Recommended)
-------------------------------------
1. Open the notebook: main.ipynb in Google Colab
2. Upload eva_social_listening_INPUT_FINAL.csv when prompted
3. Click Runtime > Run all
4. Wait 10-15 minutes for completion
5. Download output files from /output folder

METHOD 2: Local Python Environment
-----------------------------------
1. Install dependencies: pip install -r requirements.txt
2. Place input file in /data folder
3. Run: jupyter notebook main.ipynb
4. Execute all cells in order
5. Outputs will be saved in /output folder

EXPECTED RUNTIME:
On Google Colab (Free Tier - CPU):
- Cell 1-4: ~2 minutes (installation + data loading)
- Cell 5: ~2 minutes (model downloads - first time only)
- Cell 6-7: ~5 minutes (sentiment classification for 1400 mentions)
- Cell 8-9: ~1 minute (topic classification)
- Cell 10-13: ~1 minute (insights + save outputs)
- Cell 14: ~30 seconds (validation)

TOTAL: ~12-15 minutes

On Google Colab with GPU (if enabled):
TOTAL: ~8-10 minutes


OUTPUT FILES:


The pipeline generates 3 output files:

1. social_listening_output.csv
   - Per-mention classification results
   - Columns: mention_id, platform, text, sentiment, topic, relevance_score, etc.
   - 1400 rows (one per mention)

2. social_listening_output.xlsx
   - Same as CSV but in Excel format
   - Sheet name: "Sheet1"

3. insights.json
   - Aggregated insights and alerts
   - Contains: top topics, sentiment distribution, platform stats, alerts


KEY FEATURES:

✓ Bilingual Support: Arabic (60%) + English (40%)
✓ Sentiment Analysis: 68.57% accuracy (validated)
✓ Topic Classification: 10 topic categories
✓ Relevance Scoring: Brand mention detection
✓ Multi-Platform: Twitter, Facebook, Instagram, Amazon, Jumia, etc.
✓ Insights Generation: Top topics, trends, alerts
✓ Schema Compliant: Matches official challenge output format


MODELS USED:

1. Sentiment Analysis:
   - English: cardiffnlp/twitter-roberta-base-sentiment-latest
   - Arabic: CAMeL-Lab/bert-base-arabic-camelbert-msa-sentiment

2. Topic Classification:
   - Keyword-based matching (9 predefined topics + general)

3. Relevance Scoring:
   - Brand keyword detection


TROUBLESHOOTING:

ISSUE: Models not downloading
FIX: Check internet connection. Models download automatically on first run.

ISSUE: Out of memory error
FIX: Use Google Colab with GPU enabled or reduce batch size in code.

ISSUE: Sentiment accuracy lower than expected
FIX: This is normal. 68% is good for a simple pipeline. Can be improved with
     fine-tuning on domain-specific data.

ISSUE: Output files not found
FIX: Check that all cells executed successfully. Re-run Cell 13.

ISSUE: Arabic text showing as ???
FIX: Ensure UTF-8 encoding when opening files. Use encoding='utf-8-sig'.

PERFORMANCE METRICS:


Dataset Size: 1,400 mentions
Processing Speed: ~100-120 mentions/minute (CPU)
Sentiment Accuracy: 68.57% (validated against ground truth)
Languages Supported: Arabic, English
Platforms Covered: 9 (Twitter, Facebook, Instagram, etc.)
