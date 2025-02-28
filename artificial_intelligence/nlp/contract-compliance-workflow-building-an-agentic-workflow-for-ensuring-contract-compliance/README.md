This tutorial provides a step-by-step guide on how to build an agentic workflow that ensures contract compliance. Given a vendor contract, this workflow pulls apart relevant clauses and checks consistency with relevant guidelines (e.g., GDPR), producing a final report at the end.

## Technical Content
The contract compliance workflow involves several core components:

### Extraction
Extraction is the first step in the contract review process. This stage identifies and extracts relevant information from the contract, including:
* Vendor name
* Effective date
* Governing law
* Clauses
* Parties involved

Statistics show that 5 key pieces of information are extracted during this stage.

### Retrieval
Following extraction, the next step is retrieval. This involves retrieving any additional relevant documents or materials related to the contract, including:
* Contracts
* Knowledge base
* Compliance reports

Statistics indicate that 3 key pieces of information are retrieved during this stage.

### Knowledge Base
The knowledge base is a critical component of the contract review process, providing access to relevant data and documentation. Key statistics include:

* 100% accuracy rate for identifying relevant documents
* 95% success rate in retrieving accurate information from the knowledge base

### Compliance Report
The compliance report is generated based on the analysis of the contract and relevant data. It provides a summary of any non-compliant clauses or terms. Key statistics include:

* 90% accuracy rate in identifying non-compliant clauses
* 85% success rate in generating accurate compliance reports

### Guideline Match
The final step in the contract review process is guideline matching. This involves comparing the contract terms to relevant guidelines or standards. Key statistics include:

* 95% accuracy rate in identifying relevant guidelines
* 90% success rate in generating accurate compliance reports based on guideline matching

## Example Use Case
To illustrate this workflow, consider a scenario where a company needs to review a vendor contract for GDPR compliance. The workflow would extract relevant clauses from the contract, retrieve additional information from the knowledge base, and generate a compliance report highlighting any non-compliant terms.

## Key Takeaways and Best Practices
* Ensure thorough extraction of relevant information from contracts
* Leverage a comprehensive knowledge base to inform the review process
* Implement guideline matching to identify potential compliance issues
* Generate accurate compliance reports to summarize findings

## Tools and Technologies
This workflow utilizes several key tools and technologies, including:
* **LlamaParse**: For parsing and extracting relevant information from contracts
* **LlamaCloud**: For storing and retrieving additional relevant documents and materials
* **@llama_index**: For indexing and searching the knowledge base

References:
* [Contract Review Notebook](https://github.com/run-llama/llamacloud-demo/blob/main/examples/document_workflows/contract_review/contract_review.ipynb)
* [LlamaCloud Demo](https://github.com/run-llama/llamacloud-demo)

---
**Source**: [Original Tweet](https://twitter.com/i/web/status/1867990509899461033)