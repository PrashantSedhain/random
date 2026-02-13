# random
To get your POC off the ground, you need a coding agent that doesn't just write code, but understands the **relational logic** between law firms and their case histories.

Below is a professional, high-precision prompt designed for a coding agent (like Claude 3.5 Sonnet, GPT-4, or GitHub Copilot) to generate your synthetic S3 data.

---

## **Prompt for Coding Agent: Synthetic Legal Data Generation**

**Role:** You are a Senior Data Engineer specializing in AWS Bedrock Knowledge Bases and GraphRAG architectures.

**Task:** Write a Python script to generate synthetic JSON data for a Law Firm Recommendation POC. The script must create two types of files: **Firm Profiles** and **Past Claims**, including their required Amazon Bedrock metadata sidecar files.

### **1. Data Requirements**

Generate a dataset of **[X]** Law Firms and **[Y]** associated Past Claims.

* **Firm Profiles:** Must contain a `narrative_summary` describing expertise and a `graph_data` array for Neptune relationships.
* **Past Claims:** Each claim must link to a `firm_id` from the generated firms. Claims must vary in `injury_type` (e.g., Spinal, Traumatic Brain Injury, Orthopedic) and `jurisdiction` (e.g., Florida, New York, Texas).

### **2. Technical Specifications**

* **File Naming:**
* Source: `{ID}.json`
* Metadata: `{ID}.json.metadata.json` (Required for Bedrock sidecar filtering).


* **Structure:**
* **Metadata Files:** All filtering attributes must be nested inside a `"metadataAttributes"` key.
* **Data Types:** Use `String`, `Number`, and `Boolean` for metadata.


* **Output Folder:** Organize files into `/firms/` and `/claims/` directories.

### **3. Example Reference Structure**

Use the following schemas as your absolute template for the generator logic:

**Firm Schema:**

```json
// firm_001.json
{
  "firm_id": "FIRM-001",
  "firm_name": "Example Law Group",
  "narrative_summary": "A specialized litigation firm in Florida...",
  "graph_data": [
    { "subject": "Example Law Group", "predicate": "located_in", "object": "Florida" }
  ]
}
// firm_001.json.metadata.json
{
  "metadataAttributes": { "jurisdiction": "Florida", "win_rate": 0.92, "active": true }
}

```

**Claim Schema:**

```json
// claim_101.json
{
  "claim_id": "CLM-101",
  "firm_id": "FIRM-001",
  "case_narrative": "Detailed summary of a spinal injury case...",
  "relationships": [
    { "subject": "CLM-101", "predicate": "handled_by", "object": "FIRM-001" }
  ]
}
// claim_101.json.metadata.json
{
  "metadataAttributes": { "firm_id": "FIRM-001", "injury_type": "Spinal", "payout": 500000 }
}

```

### **4. Execution Prompt**

"Now, generate the Python script using `faker` or `random` libraries to produce this data. Ensure the narratives are diverse and professional. Save the output to a local folder named `s3_mock_data`."

---
