# Automated-Form

## Run

```bash
pip install -r requirements.txt
streamlit run app.py
```

The app uses `sample.docx` as its built-in template. Ensure this file is committed to GitHub; it is required by the deployed app.

For persistent company profiles on Streamlit Community Cloud, add these secrets:

```toml
GITHUB_TOKEN = "github_pat_..."
GITHUB_REPOSITORY = "your-user/your-repository"
GITHUB_BRANCH = "main"
GITHUB_DATA_DIR = "companies"
```

The token needs repository **Contents: Read and write** permission. The app commits each company create, edit, and delete directly to the configured branch. Without these secrets it uses local JSON files, which are temporary on Streamlit Cloud.

DOCX downloads work with the Python dependencies in `requirements.txt`. PDF downloads convert the generated DOCX with LibreOffice so the PDF keeps the same format as the Word document.

Existing profiles can be edited from the company list. The completed certificate can be downloaded as Word, PDF, or a text summary, and the summary can be shared through WhatsApp, Telegram, or email. Attach the downloaded Word or PDF file separately when sending it through a messaging service.

Each company profile includes a `Kepada` choice for Melaka or Selangor. Existing profiles without this field use Melaka by default. Each choice inserts its corresponding recipient address into the certificate.

For Streamlit deployments, `packages.txt` installs LibreOffice automatically.
For a local Ubuntu installation, run:

```bash
sudo apt install libreoffice
```