# OWASP PDF v5.0.0 Installation

1. Click [Download ZIP](https://github.com/tetsuoseto/AISVS/archive/refs/heads/main.zip) link to download the all-in-one zip file, AISVS-main.zip (143MB) on your Ubuntu Desktop 24.04.2 LTS or Ubuntu instance on cloud. The zip file contains the original AISVS repo + the owasp_pdf_5 build environment: `AISVS-main/1.0/blddoc` directory.

2. Open terminal window, `cd` to `AISVS-main/1.0/blddoc` directory and run `shasum -a 256 owasp_pdf` to calculate the sha256 hash code of `owasp_pdf` executable. It should match fbe47467c3be4431251be42825effc4ecd2163b43bcfea314544a8414bbb2b3e

3. Make sure all the source MD files under `AISVS-main/1.0/blddoc/asv/` are symbolic-linked to the original MD files on `AISVS-main/1.0/en/` Note that the source MD file (symbolic link) names follow owasp_pdf naming convention, e.g., `ASV1001_0x01-Frontispiece.md` for `0x01-Frontispiece.md`.

4. Run `./owasp_pdf -v` in the terminal window to verify the installation.

5. Run `./owasp_pdf -y -l ASV_<lang>` in the terminal window and verify a PDF is built. You can set your choice of registered language from './owasp_pdf -r', e.g, `./owasp_pdf -y -l ASV_en-US`

```
$ cd ~/AISVS-main/1.0/blddoc
$ shasum -a 256 owasp_pdf
fbe47467c3be4431251be42825effc4ecd2163b43bcfea314544a8414bbb2b3e  owasp_pdf
$ ./owasp_pdf -v
OWASP_PDF Version: OWASP PDF v5.0.0 20250814-211728
$ ./owasp_pdf -y -l ASV_en-US
*** initializing owasp_pdf build environment...
*** Loaded 'owasp_pdf_register_ASV_plugin'
*** Processing ASV_en-US
        2,575 lines written to ~/AISVS-main/1.0/blddoc/asv/en-US/baseline/ASVAll_en-US.md
        91 page PDF created on ~/AISVS-main/1.0/blddoc/asv/en-US/baseline/ASVAll_en-US.pdf
    Processing time: 173 seconds
```

# Machine Translation with OWASP PDF 5

1. Get access to Ubuntu on your local linux box or Ubuntu instance on cloud. Tested on Ubuntu Desktop 24.04.2 LTS.  Should work on cloud as well.
2. Get API key of OpenAI Platform and set it to env.variable:TRANSLATE_ACCESS_KEY. Buy $5 or $10 credit initially. We use GPT-4.1 or GPT-5. One ASV language round costs 25 cents or less.
3. When you install OWASP PDF 5, easiest is [Download ZIP](https://github.com/tetsuoseto/AISVS/archive/refs/heads/main.zip) -- AISVS-main.zip (143MB) contains everything you need. Follow the OWASP PDF v5.0.0 Installation steps above and verify the installation.
4. Pick your language, e.g, de-DE and run the ./owasp_pdf command with `--mt gpt-4.1-nano` option.

```
$ cd ~/AISVS-main/1.0/blddoc
$ ./owasp_pdf --mt gpt-4.1-nano -l ASV_de-DE
*** Initializing owasp_pdf build environment...
*** Loaded 'owasp_pdf_register_ASV_plugin'
*** Processing ASV_de-DE
        2,596 lines written to ~/AISVS-main/1.0/blddoc/asv/de-DE/baseline/ASVAll_de-DE.md
        92 page PDF created on ~/AISVS-main/1.0/blddoc/asv/de-DE/baseline/ASVAll_de-DE.pdf
    Processing time: 1,565 seconds
```

## OWASP PDF 5 Command Options

#### Help (-h)
```
$ ./owasp_pdf -h
```
#### Registered Projects and Languages (-r)
```
$ ./owasp_pdf -r
```
#### Build PDF of One Language (-l)
```
$ ./owasp_pdf -l ASV_en-US
```
#### Build PDF of One Language with Auto-Hyphenation (-y)
```
$ ./owasp_pdf -l ASV_en-US -y
```
#### Build PDFs of All the Registered Languages (-a)
```
$ ./owasp_pdf -a ASV
```
#### Machine Translate and Build PDF of One Language (--mt)
```
$ ./owasp_pdf --mt gpt-4.1-nano -l ASV_de-DE
```
#### Run English Grammar and Spell Check, then Build PDF (--mt, -e)
```
$ ./owasp_pdf --mt gpt-4.1-nano -e -l ASV_en-US
```
#### Run English Grammar and Spell Check, then Build PDF with Auto-Hyphenation (--mt, -e, -y)
```
$ ./owasp_pdf --mt gpt-4.1-nano -e -l ASV_en-US -y
```
#### Full Fledged Build (--mt, -e, -y, -a)
Run English Grammar and Spell Check, Machine Translate All the Registered Languages, then Build PDFs with Auto-Hyphenation. Note that grammar/spell check of US English MD files is done first, then machine translate non-English languages.
```
$ ./owasp_pdf --mt gpt-4.1-mini -e -a ASV -y
```
#### Build PDF from pre-translated MD files (-x)
If '--mt' is also specified, '-x' has precedence; MT won't be done.
```
$ ./owasp_pdf -l ASV_de-DE -x
```

# Directory Structure of AISVS project repo with owasp_pdf_5 build environment

There are 16 directories, 76 files under AISVS-main. `blddoc` directory is the owasp_pdf_5 build environment. Everything else is exactly what's in [the AISVS project repository](https://github.com/OWASP/AISVS).

```
AISVS-main
├── 1.0
│   ├── Makefile
│   ├── blddoc
│   │   ├── LICENSE
│   │   ├── README.md
│   │   ├── asv
│   │   │   ├── ASV1001_0x01-Frontispiece.md -> ../../en/0x01-Frontispiece.md
│   │   │   ├── ASV1002_0x02-Preface.md -> ../../en/0x02-Preface.md
│   │   │   ├── ASV1003_0x03-Using-AISVS.md -> ../../en/0x03-Using-AISVS.md
│   │   │   ├── ASV1101_0x10-C01-Training-Data-Governance.md -> ../../en/0x10-C01-Training-Data-Governance.md
│   │   │   ├── ASV1102_0x10-C02-User-Input-Validation.md -> ../../en/0x10-C02-User-Input-Validation.md
│   │   │   ├── ASV1103_0x10-C03-Model-Lifecycle-Management.md -> ../../en/0x10-C03-Model-Lifecycle-Management.md
│   │   │   ├── ASV1104_0x10-C04-Infrastructure.md -> ../../en/0x10-C04-Infrastructure.md
│   │   │   ├── ASV1105_0x10-C05-Access-Control-and-Identity.md -> ../../en/0x10-C05-Access-Control-and-Identity.md
│   │   │   ├── ASV1106_0x10-C06-Supply-Chain.md -> ../../en/0x10-C06-Supply-Chain.md
│   │   │   ├── ASV1107_0x10-C07-Model-Behavior.md -> ../../en/0x10-C07-Model-Behavior.md
│   │   │   ├── ASV1108_0x10-C08-Memory-Embeddings-and-Vector-Database.md -> ../../en/0x10-C08-Memory-Embeddings-and-Vector-Database.md
│   │   │   ├── ASV1109_0x10-C09-Orchestration-and-Agentic-Action.md -> ../../en/0x10-C09-Orchestration-and-Agentic-Action.md
│   │   │   ├── ASV1110_0x10-C10-Adversarial-Robustness.md -> ../../en/0x10-C10-Adversarial-Robustness.md
│   │   │   ├── ASV1111_0x10-C11-Privacy.md -> ../../en/0x10-C11-Privacy.md
│   │   │   ├── ASV1112_0x10-C12-Monitoring-and-Logging.md -> ../../en/0x10-C12-Monitoring-and-Logging.md
│   │   │   ├── ASV1113_0x10-C13-Human-Oversight.md -> ../../en/0x10-C13-Human-Oversight.md
│   │   │   ├── ASV1200_0x90-Appendix-A_Glossary.md -> ../../en/0x90-Appendix-A_Glossary.md
│   │   │   ├── ASV1201_0x91-Appendix-B_References.md -> ../../en/0x91-Appendix-B_References.md
│   │   │   ├── ASV1202_0x92-Appendix-C_Governance_and_Documentation.md -> ../../en/0x92-Appendix-C_Governance_and_Documentation.md
│   │   │   ├── ASV1203_0x93-Appendix-D_AI_for_Code_Generation.md -> ../../en/0x93-Appendix-D_AI_for_Code_Generation.md
│   │   │   └── ASV1204_0x94-Appendix-E_Example_Tools_and_Frameworks.md -> ../../en/0x94-Appendix-E_Example_Tools_and_Frameworks.md
│   │   ├── owasp_pdf
│   │   ├── owasp_pdf_data_ASV
│   │   │   ├── appendix_pages
│   │   │   ├── baseline
│   │   │   │   ├── custom_data_ASV_en-ZZ.json
│   │   │   │   └── images
│   │   │   │       └── license.png
│   │   │   └── templates
│   │   │       ├── image_parts
│   │   │       └── page_pdfs
│   │   ├── owasp_pdf_register_ASV_plugin.py
│   │   └── version_time_stamp.txt
│   ├── en
│   │   ├── 0x00-Header.yaml
│   │   ├── 0x01-Frontispiece.md
│   │   ├── 0x02-Preface.md
│   │   ├── 0x03-Using-AISVS.md
│   │   ├── 0x10-C01-Training-Data-Governance.md
│   │   ├── 0x10-C02-User-Input-Validation.md
│   │   ├── 0x10-C03-Model-Lifecycle-Management.md
│   │   ├── 0x10-C04-Infrastructure.md
│   │   ├── 0x10-C05-Access-Control-and-Identity.md
│   │   ├── 0x10-C06-Supply-Chain.md
│   │   ├── 0x10-C07-Model-Behavior.md
│   │   ├── 0x10-C08-Memory-Embeddings-and-Vector-Database.md
│   │   ├── 0x10-C09-Orchestration-and-Agentic-Action.md
│   │   ├── 0x10-C10-Adversarial-Robustness.md
│   │   ├── 0x10-C11-Privacy.md
│   │   ├── 0x10-C12-Monitoring-and-Logging.md
│   │   ├── 0x10-C13-Human-Oversight.md
│   │   ├── 0x90-Appendix-A_Glossary.md
│   │   ├── 0x91-Appendix-B_References.md
│   │   ├── 0x92-Appendix-C_Governance_and_Documentation.md
│   │   ├── 0x93-Appendix-D_AI_for_Code_Generation.md
│   │   ├── 0x94-Appendix-E_Example_Tools_and_Frameworks.md
│   │   └── Categories.md
│   ├── images
│   │   ├── license.png
│   │   ├── owaspLogo.png
│   │   ├── owasp_logo_1c_notext.png
│   │   └── owasp_logo_header.png
│   ├── mappings
│   │   ├── README.md
│   │   ├── nist.md
│   │   └── v1.0.be_cwe_mapping.json
│   ├── templates
│   │   ├── eisvogel.tex
│   │   ├── header-eisvogel.tex
│   │   └── reference.docx
│   └── tools
│       ├── aisvs.py
│       ├── cyclonedx.py
│       ├── export.py
│       ├── generate_document.sh
│       └── install_deps.sh
├── CONTRIBUTING.md
├── LICENSE.md
├── Makefile
├── README.md
├── Security.md
├── docker
│   ├── Dockerfile
│   └── run.sh
├── generate-all.sh
└── hall_of_fame.md
```
