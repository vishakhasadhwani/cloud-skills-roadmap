# Advanced Differentiation Skills

**Focus:** Multi-cloud Terraform, cost optimization, and hybrid AI. Use these once you’re comfortable with the core roadmap.

---

## Multi-Cloud Terraform

### Modules

- [Terraform Registry](https://registry.terraform.io/)
- [Advanced Terraform modules (HashiCorp)](https://developer.hashicorp.com/terraform/tutorials/modules)

### Multi-cloud examples

- [Terraform AWS provider](https://github.com/hashicorp/terraform-provider-aws)
- [GCP Terraform examples](https://github.com/GoogleCloudPlatform/terraform-google-examples)

### Patterns

- [Terraform best practices](https://www.terraform-best-practices.com/)
- [Module composition](https://developer.hashicorp.com/terraform/language/modules/develop/composition)

---

## Cost Optimization

### FinOps

- [FinOps Foundation](https://www.finops.org/introduction/what-is-finops/)
- [FinOps Certified Practitioner](https://www.finops.org/certification/)

### Pricing tools

- [AWS Pricing Calculator](https://calculator.aws/)
- [Azure Pricing Calculator](https://azure.microsoft.com/en-us/pricing/calculator/)
- [GCP Pricing Calculator](https://cloud.google.com/products/calculator)

### Case studies

- [AWS cost optimization](https://aws.amazon.com/architecture/cost-optimization/)
- [CloudZero blog](https://www.cloudzero.com/blog)

---

## Hybrid AI Architecture

### RAG + private AI

- [RAG (Qdrant)](https://qdrant.tech/rag/)
- [Private AI / RAG](https://www.saiumesh.dev/posts/rag-2)
- [Hybrid LLM: local + cloud (Ollama Minions)](https://ollama.ai/blog/minions)

### Privacy-first AI

- [Ollama (on-prem LLMs)](https://github.com/ollama/ollama)
- [Secure RAG (Qdrant)](https://qdrant.tech/documentation/examples/rag-chatbot-vultr-dspy-ollama/)

### ML monitoring

- [Prometheus overview](https://prometheus.io/docs/introduction/overview/)
- [ML monitoring](https://www.jeremyjordan.me/ml-monitoring/)


### Advanced Project: Intelligent LLM Query Router

**Detailed Steps:**

1. **Create query classifier:** Categorize queries as simple/complex/sensitive
2. **Setup routing logic:**
   - Simple → Ollama (local, fast, free)
   - Complex → GPT-4 (expensive, powerful)
   - Sensitive → On-prem only (never leaves network)
3. **Implement caching:** Redis cache for repeated queries
4. **Add metrics:** Track latency, cost, and accuracy per route
5. **Document results:**
   - 75% cost reduction vs all-API approach
   - 80% queries under 100ms

**Skills That Set You Apart:**

- ✅ Multi-Cloud Terraform expertise (not just "AWS expert")
- ✅ Cost optimization obsession (can you build it for 1/10th the price?)
- ✅ Hybrid AI architecture patterns
- ✅ Understanding trade-offs (not dogmatic about any approach)

---

[← Back to roadmap](../README.md) · [Resources](../Resources/)
