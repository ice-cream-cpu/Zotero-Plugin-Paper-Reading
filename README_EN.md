# ice-cream v0.6.4

**Language: [简体中文](README.md) | English**

ice-cream is an AI-assisted paper reading plugin for Zotero. It lets you work with one or multiple papers using full text, original PDFs, rendered page images, and continuous conversations to explain equations, interpret figures and tables, compare papers, and organize notes.

## Download

- [Download ice-cream 0.6.4](https://raw.githubusercontent.com/ice-cream-cpu/Zotero-Plugin-Paper-Reading/main/release-assets/ice-cream-0.6.4.xpi)
- File: `ice-cream-0.6.4.xpi`
- SHA-256: `048b3ecd3b908967301d2200be479c5207ec483d21c3f2cf027bd380d17d790e`
- Compatible with Zotero `9.0` and later; currently verified with Zotero `10.0.6`

## Core Features

- **Full-text paper Q&A**: Reads Zotero item metadata, abstracts, and PDF full text, then locates pages relevant to your question.
- **PDF and visual understanding**: Sends original PDFs to compatible models and automatically uses relevant rendered page images when a model or endpoint cannot accept PDFs.
- **Multi-paper workspace**: Repeated `Use Selection` actions accumulate and deduplicate papers for comparing methods, experiments, and conclusions.
- **Continuous conversation memory**: Every turn includes the current text conversation history and retrieves new question-relevant evidence from papers already associated with the conversation.
- **Precise content retrieval**: Combines exact numbered-reference matching, heading and caption recognition, adjacent-page expansion, and relevance reranking for tables, figures, equations, and sections.
- **Clear source citations**: Responses can use labels such as `[S1:p2]` and `[S2:A2:p5]` to identify the paper, attachment, and page.
- **Markdown and math rendering**: Supports structured Markdown, code blocks, tables, and KaTeX-rendered equations.
- **Local conversation management**: Automatically saves text conversations so you can switch histories, continue asking questions, or permanently delete an entry.
- **Zotero note saving**: `Save Note` stores the current conversation as a child note under the selected paper when possible.
- **Flexible window**: Move and resize the assistant window freely, or use the pin button to keep it above other windows.

## Distinctive Capabilities

### Add Once, Continue Asking

After you click `Use Selection`, the papers become part of the current conversation. The first paper-enabled question can include full text and visual evidence. Later questions retain the conversation history and retrieve the most relevant pages locally instead of repeatedly uploading the entire PDF. This preserves context while reducing unnecessary transfers.

### Automatic PDF and Page-Image Fallback

For models that support original PDFs, ice-cream sends the PDF directly. If the selected model or API endpoint rejects the PDF, the plugin renders relevant pages as images and retries, allowing figures, tables, equations, and page layout to remain part of the evidence.

### Retrieval Designed for Figures, Tables, and Equations

When you ask about “Table 3,” “Figure 9,” “Equation (38),” or a named section, ice-cream prioritizes exact numbers, headings, and captions, expands to nearby pages, and reranks the evidence. This reduces cases where a text fragment is found but the complete figure or table is missed.

## Installation

1. Download the `.xpi` file above.
2. Open Zotero and go to **Tools → Plugins**.
3. Click the gear button in the upper-right corner of the Add-ons Manager.
4. Choose **Install Add-on From File**.
5. Select `ice-cream-0.6.4.xpi`, confirm the installation, and restart Zotero.

After installation, the **ice-cream** launcher appears in the lower-right corner of the Zotero main window.

## First-Time Setup

Open ice-cream and expand **Settings**:

1. Choose a model provider under **Provider**.
2. Enter the provider's key under **API key**.
3. Choose a model from the **Model** menu, or enter a model name offered by a compatible endpoint.
4. When using a custom or compatible API, verify that **Endpoint** matches the provider's documentation.
5. Set **Context characters** as needed. This is the extracted-paper text budget available to one request.
6. Choose whether new conversations include metadata, full text, and PDFs.

ice-cream supports OpenAI, Claude, DeepSeek, Qwen, and OpenAI-compatible endpoints. Model names and endpoint capabilities may change over time, so use the options available to your API account and follow the provider's current documentation.

## Basic Usage

1. Select a paper in Zotero or open it in the Zotero reader.
2. Click **ice-cream** in the lower-right corner to open the assistant.
3. Click **Use Selection** to add the current paper to the conversation.
4. Enter a question and send it, for example: “Summarize the method,” “Explain Equation (12),” or “Interpret Figure 4 and describe its conclusion.”
5. Ask follow-up questions directly. You do not need to click `Use Selection` again unless you want to add papers or explicitly attach paper content again.

While a request is running, the window displays the active model, processing stage, and elapsed time. After the response finishes, it displays the total time. You can stop an active request or restore and edit your latest question before sending it again.

## Comparing Multiple Papers

Select multiple papers in Zotero and click `Use Selection`, or open papers one by one and click `Use Selection` for each. The plugin accumulates sources in the current workspace, removes duplicates, and can retain up to 12 sources.

The `Pinned research workspace` status shows how many sources are currently attached. You can then ask questions such as:

- “Compare the system models and key assumptions in these papers.”
- “Summarize the datasets, evaluation metrics, and main results of each paper.”
- “Under what conditions do these methods reach different conclusions?”

Clicking `Clear` ends the current conversation, deletes its local conversation record, and creates a new empty conversation.

## PDF and Full-Text Options

- **Metadata**: Sends the title, authors, date, DOI, abstract, and other Zotero item information.
- **Full text**: Sends extracted paper text and makes it available for relevant-page retrieval in later turns.
- **PDF**: Attaches original PDFs or compatible rendered page images to the next question armed with `Use Selection`.
- **Context characters**: Controls the maximum extracted-text budget for a request. A larger value generally covers more material but uses more model context.

A single request can attach up to 8 original PDFs. Each file can be up to 64 MB, with a combined limit of 120 MB. When these thresholds are exceeded, the plugin still attempts to provide evidence through extracted text and relevant rendered pages.

## Conversation History

- Text conversations are saved automatically and named from their topic.
- Use the conversation menu at the top of the window to switch to an earlier conversation and continue asking questions.
- Use the circled X button beside a history entry to delete it permanently.
- `Clear` deletes the active conversation's local text history and starts a new conversation.
- To avoid unnecessary storage use, conversation history does not contain PDF files or full-text copies. When you reopen a conversation, ice-cream reads the papers again through their recorded Zotero item references.

## Save Note

Click **Save Note** to save the current conversation as a Zotero note:

- When a regular bibliographic item is selected, the note is saved as its child note.
- When a PDF attachment is selected, the note is preferably saved under its parent bibliographic item.
- When no suitable parent item is available, it is saved as a standalone note.

You can find the saved result in Zotero's **Notes** pane or in the selected item's child-item list.

## Equations and Tables

ice-cream instructs models to use valid Markdown/LaTeX equation syntax and renders it with KaTeX. Inline equations use `$...$`, while display equations use `$$...$$`. Tables are laid out from their Markdown structure, with horizontal scrolling available for genuinely wide content.

If equations in the original PDF are scanned, use unusual font encoding, or have a complex layout, include the equation, figure, or table number and page in your question. The plugin will prioritize that location and attach visual evidence from nearby pages.

## Local Data and Privacy

- Conversation text is stored in your local Zotero data directory.
- PDF files and extracted full text are not copied into conversation history files.
- API keys are stored in Zotero's local preferences and are not written to the GitHub repository.
- Paper content and questions are sent to the configured model API only when you initiate a request. Consider the confidentiality of each paper and the provider's privacy policy before uploading it.

## Automatic Updates

The plugin includes a Zotero update URL. When a new version is published, Zotero can check `updates.json` for a compatible update. You can also download the latest XPI from this repository and install it over the existing version.
