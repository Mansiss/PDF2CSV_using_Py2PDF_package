# PDF2CSV_using_Py2PDF_package

## code is here
```
import csv
import PyPDF2

def extract_sentences_from_pdf(pdf_path):
    sentences = []

    # Open the PDF file
    with open(pdf_path, 'rb') as file:
        pdf_reader = PyPDF2.PdfReader(file)

        # Iterate over each page in the PDF
        for page in pdf_reader.pages:
            # Extract text from the page
            text = page.extract_text()

            # Split the text into sentences
            sentences += text.split('. ')

    return sentences


def save_sentences_to_csv(sentences, csv_path):
    with open(csv_path, 'w', newline='',encoding="utf-8") as file:
        writer = csv.writer(file)

        # Write each sentence as a separate row in the CSV file
        for sentence in sentences:
            writer.writerow([sentence])


# PDF file path
pdf_path = 'input.pdf'

# CSV file path to save the sentences
csv_path = 'output.csv'

# Extract sentences from the PDF
sentences = extract_sentences_from_pdf(pdf_path)

# Save sentences to CSV
save_sentences_to_csv(sentences, csv_path)

```
