# AI Customer Support & FAQ Automation

### Intelligent Customer Support Using n8n, Google Gemini & Notion

## Project Overview

An AI-powered customer support automation workflow built with n8n to handle customer inquiries, generate FAQ-based answers, classify requests, assign priorities, and escalate unresolved questions to human support through Notion.

The workflow integrates Google Gemini through a REST API and uses conditional routing to determine whether a customer can receive an automated response or requires human assistance.

## Problem

Customer support teams often spend time answering repetitive questions and manually organizing support requests.

This project demonstrates how AI and workflow automation can reduce repetitive tasks while preserving a human escalation path for questions that cannot be answered from approved FAQ information.

## Solution

The workflow:

1. Receives customer questions through an HTTP webhook.
2. Extracts the customer's name and question.
3. Sends the question and predefined FAQ knowledge to Google Gemini.
4. Generates an answer and assigns a category and priority.
5. Determines whether human support is required.
6. Returns an automated answer when the FAQ contains the necessary information.
7. Creates a Notion support ticket when human assistance is needed.
8. Sends a confirmation response to the customer.

## Technologies Used

- **n8n:** Workflow orchestration
- **Google Gemini API:** AI-powered question answering and classification
- **Notion:** Support ticket management
- **Webhooks:** Receiving customer requests
- **REST API / HTTP Request:** AI service integration
- **JSON:** Structured data exchange

## Workflow Architecture

**Automated Response Path**

Webhook → Prepare Customer Request → Gemini AI Support Agent → Prepare AI Result → Needs Human Support? → Route Support Category → Send Customer Response

**Human Escalation Path**

Needs Human Support? → Create Support Ticket → Human Support Response

## Key Features

- FAQ-grounded AI responses
- Automated request classification
- Priority assignment (High, Medium, Low)
- Conditional routing based on human support requirements
- Notion ticket creation
- JSON responses through webhooks
- Retry configuration for Gemini API requests

## Example Input

```json
{
  "customerName": "Ahmad",
  "question": "How can I reset my password?"
}
```

## Example Automated Response

```json
{
  "success": true,
  "answer": "You can reset your password by clicking Forgot Password on the login page.",
  "category": "Technical Support",
  "priority": "Low"
}
```

*Illustrative response; actual classification and wording depend on Gemini.*

## Human Escalation

When the requested information is not available in the FAQ, the AI is instructed not to invent an answer.

Instead, the workflow creates a support ticket in Notion with the customer's question, request category, priority, and review status.

The customer receives a confirmation that the request has been forwarded to the support team.

## Setup Requirements

1. Import the workflow JSON into n8n.
2. Configure Google Gemini API credentials.
3. Connect a Notion account.
4. Create a Notion database with the required support ticket properties.
5. Update the workflow's Notion database reference.
6. Customize the sample FAQ knowledge.
7. Configure and activate the webhook.
8. Test both automated-response and human-escalation paths.

## Project Status

Core workflow implemented and exported.

Final end-to-end testing, error-handling validation, and production-readiness checks remain to be documented.

## Future Improvements

- External FAQ knowledge base
- Input validation
- Dedicated API error handling
- Customer email notifications
- Support analytics and reporting
- Human ticket resolution tracking

## Security

API credentials must be configured securely within n8n. Do not commit API keys, tokens, customer data, or other sensitive information to this repository.
