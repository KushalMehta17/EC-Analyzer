# Earnings Call Transcript Analyzer

This project focuses on extracting and analyzing insights from earnings call transcripts of publicly listed companies. These transcripts are often rich in information, as they contain direct communication between company officials and market analysts. Our goal was to process this unstructured data to better understand how companies present themselves during these calls, especially how sentiment and communication align (or misalign) with actual market behavior.

## Approach

1. **Data Collection**  
   - Scraped earnings call transcripts in PDF form from [Screener.in](https://www.screener.in/) for selected companies.
   - Targeted companies from varied domains: Relaxo (footwear), Ethos (luxury watches), and Globus Spirits (alcohol).

2. **PDF Parsing & Dialogue Extraction**  
   - Parsed transcripts using `pdfplumber` to extract raw text.
   - Used regular expressions to detect speakers and segment dialogues.

3. **Speaker Role Classification**  
   - Used a local language model (specifically, 'Llama 3.1' via 'Ollama') to classify each speaker as CEO, Analyst, Moderator, or Investor.
   - This helped structure the unformatted text into clear, labeled dialogues.

4. **Sentiment Analysis**  
   - For each analyst question and company answer pair, applied a pre-trained sentiment model from Hugging Face, which was selected as the 'distilroberta-base' after rigorous trial and error of several models.
   - Focused on cases where company responses seemed mismatched with analyst tone (e.g., evasive or overly positive answers).

5. **Market Comparison**  
   - Pulled historical stock prices and volumes using the `yfinance` library.
   - Visualized how sentiment from the call related to market movement in the following days.

## Key Insights

- Found partial alignment between company tone and post-call market behavior, especially in Globus Spirits' Q1 call.
- Confirmed that while earnings call sentiment is not a definitive predictor, it offers valuable directional guidance.

## Tools Used

- Python, Requests, BeautifulSoup, pdfplumber, Regex
- Ollama, LLaMA 3.1 (for role classification)
- Hugging Face Transformers (DistilRoBERTa for sentiment)
- yfinance (for stock price and volume data)

## Future Work

- Add sector-wide analysis with more companies
- Deploy a dashboard for real-time transcript analysis
- Explore fine-tuning models for company-specific language

Please explore the final codebase file and the results to know more!

