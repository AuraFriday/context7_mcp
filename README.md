# Context7 — Always-Current Library Documentation

Instant provision to your AI of current API and documentation for thousands of libraries.

> **Any library. Current docs. Code examples included.** Your AI never works with outdated documentation again.

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey.svg)](https://github.com/AuraFriday/mcp-link-server)

---

## Benefits

### 1. 📚 Always Up-to-Date
**Not cached docs — live from source.** Context7 maintains current documentation for thousands of libraries. No stale examples, no deprecated APIs.

### 2. 🎯 Focused on Your Topic
**Not entire docs — relevant sections.** Specify a topic, get focused documentation. No wading through unrelated content.

### 3. 🔍 Smart Library Resolution
**Not exact names — intelligent search.** Search "autodesk", find "autodesk-forge", "autodesk-revit", "autodesk-autocad". Discover the right library fast.

---

## Why This Tool Changes Development

**Documentation goes stale fast.** Libraries update weekly. Your cached docs from last month? Already outdated. New features missing, deprecated methods still shown.

**AI training data is months old.** Even the best AI models have knowledge cutoff dates. They can't know about libraries released last week or APIs updated yesterday.

**Finding the right docs is tedious.** Is it "react" or "reactjs"? "tensorflow" or "tensorflow-gpu"? Guessing library IDs wastes time.

**This tool solves all of that.**

Search by name → Get exact library IDs → Fetch current docs → Optionally focus on specific topics.

Your AI always has the latest documentation. No guessing, no staleness, no outdated examples.

---

## About Context7 Service

**This tool integrates with Context7** — a third-party service that provides always-current library documentation.

🌐 **Service Provider:** [Context7.com](https://context7.com/)  
📜 **Terms of Service:** By using this tool, you agree to comply with [Context7's Terms of Service](https://context7.com/terms)  
🔒 **Privacy:** Your queries remain on your local machine; only derived topics are sent to Context7's servers  
💰 **Pricing:** Free tier available; see [Context7 Plans & Pricing](https://context7.com/docs/plans-pricing)

**Important Notes:**
- Context7 is an independent service operated by Context7.com
- This MCP-Link tool provides integration with Context7's API
- Context7's service availability, rate limits, and terms are subject to their policies
- Documentation quality and coverage depend on Context7's service

**MCP-Link Integration Benefits:**
- Zero configuration required (no API key setup needed for basic use)
- Seamless integration with all MCP-Link tools
- Works out of the box with free tier
- Automatic error handling and fallbacks

### Get MCP-Link (Free)

**This tool is part of MCP-Link** — the free desktop server from [aurafriday.com](https://aurafriday.com/)

🎁 **Completely Free** • No subscriptions • No accounts  
🖥️ **One-Click Install** • Windows, Mac, Linux  
🔗 **Context7 Integration Included** • Works immediately after install

---

## Real-World Story: The Deprecated API Disaster

**The Problem:**

A developer was building an integration with the Stripe API. Their AI assistant provided code examples based on training data from 6 months ago.

The code used `stripe.Customer.create()` with parameters that had been deprecated 3 months ago. The new API required different parameter names and structure.

**Result:** 4 hours of debugging. "Why doesn't this work?" Frustration. Lost productivity.

**With This Tool:**

```python
# 1. Find the exact library ID
libraries = resolve_library_id(library_name="stripe")
# Returns: ["stripe-python", "stripe-node", "stripe-ruby", ...]

# 2. Get current documentation focused on customer creation
docs = get_library_docs(
    context7_compatible_library_id="stripe-python",
    topic="customer creation",
    tokens=5000
)

# 3. AI now has current API documentation
# Generates code with correct, current API calls
```

**Result:** Code works first time. Zero debugging. Current API patterns used correctly.

**The kicker:** Same approach now works for any library. Autodesk Forge updated? Get current docs. New React hooks? Get current docs. TensorFlow 2.x changes? Get current docs.

---

## The Complete Feature Set

### Library Resolution

**Find Libraries by Name:**
```python
# Search for libraries
results = resolve_library_id(library_name="autodesk")

# Returns list of matching libraries:
# [
#   "autodesk-forge",
#   "autodesk-revit-api",
#   "autodesk-autocad",
#   ...
# ]
```

**Why resolution matters:** Library names aren't always obvious. "tensorflow" vs "tensorflow-gpu" vs "tensorflow-js". Resolution finds all variants, you pick the right one.

### Documentation Retrieval

**Get Current Docs:**
```python
# Fetch documentation
docs = get_library_docs(
    context7_compatible_library_id="react",
    tokens=10000
)

# Returns: Current documentation text (up to 10K tokens)
```

**Focused Documentation:**
```python
# Get docs focused on specific topic
docs = get_library_docs(
    context7_compatible_library_id="stripe-python",
    topic="webhooks",
    tokens=5000
)

# Returns: Documentation relevant to webhooks only
```

**Token Control:**
```python
# Control documentation size
docs = get_library_docs(
    context7_compatible_library_id="tensorflow",
    tokens=20000  # Larger context for complex libraries
)
```

**Why topic focus matters:** Full library docs can be massive. React docs are 100K+ tokens. You don't need all of it. Focus on "hooks" or "context API" or "server components" — get exactly what you need.

---

## Usage Examples

### Resolve Library ID
```json
{
  "input": {
    "operation": "resolve-library-id",
    "library_name": "autodesk",
    "tool_unlock_token": "YOUR_TOKEN"
  }
}
```

### Get Library Documentation
```json
{
  "input": {
    "operation": "get-library-docs",
    "context7_compatible_library_id": "react",
    "tokens": 10000,
    "tool_unlock_token": "YOUR_TOKEN"
  }
}
```

### Get Focused Documentation
```json
{
  "input": {
    "operation": "get-library-docs",
    "context7_compatible_library_id": "stripe-python",
    "topic": "customer creation",
    "tokens": 5000,
    "tool_unlock_token": "YOUR_TOKEN"
  }
}
```

---

## Advanced Use Cases

### Multi-Library Integration

```python
# Building integration between multiple libraries
# Get current docs for each

# 1. Resolve library IDs
stripe_libs = resolve_library_id("stripe")
react_libs = resolve_library_id("react")

# 2. Get focused docs for each
stripe_docs = get_library_docs(
    context7_compatible_library_id="stripe-python",
    topic="payment intents",
    tokens=5000
)

react_docs = get_library_docs(
    context7_compatible_library_id="react",
    topic="hooks and state management",
    tokens=5000
)

# 3. AI now has current docs for both
# Can generate integration code with current APIs
```

### Version-Specific Documentation

```python
# Need docs for specific version?
# Context7 typically provides current stable version

# Search for version-specific library IDs
libs = resolve_library_id("tensorflow")
# May return: ["tensorflow", "tensorflow-2.x", "tensorflow-1.x"]

# Get docs for specific version
docs = get_library_docs(
    context7_compatible_library_id="tensorflow-2.x",
    tokens=10000
)
```

### Progressive Documentation Loading

```python
# Start with overview, get details as needed

# 1. Get high-level overview (small token count)
overview = get_library_docs(
    context7_compatible_library_id="django",
    tokens=2000
)

# 2. Based on user needs, get focused details
if user_needs_auth:
    auth_docs = get_library_docs(
        context7_compatible_library_id="django",
        topic="authentication",
        tokens=5000
    )

if user_needs_orm:
    orm_docs = get_library_docs(
        context7_compatible_library_id="django",
        topic="models and ORM",
        tokens=5000
    )
```

---

## Technical Architecture

### Context7 Service

**Maintained Documentation:**
- Thousands of libraries covered
- Updated regularly from source
- Code examples included
- API references current

**Smart Extraction:**
- Topic-based filtering
- Relevance ranking
- Token-aware truncation
- Code example prioritization

### Response Format

**Library Resolution:**
```json
{
  "libraries": [
    "autodesk-forge",
    "autodesk-revit-api",
    "autodesk-autocad"
  ]
}
```

**Documentation Retrieval:**
```json
{
  "library_id": "react",
  "documentation": "# React Documentation\n\n## Hooks\n\n...",
  "tokens_returned": 9847,
  "source_url": "https://react.dev/reference/react",
  "last_updated": "2025-01-15"
}
```

---

## Performance Considerations

### API Call Speed
- Library resolution: ~200-500ms
- Documentation fetch: ~500-1500ms (depends on size)
- Topic filtering: Adds ~100-300ms

### Token Limits
- Default: 10,000 tokens
- Minimum: 1,000 tokens
- Maximum: 50,000 tokens (for large libraries)
- Smart truncation if content exceeds limit

### Caching
- Context7 caches documentation server-side
- Updates propagate within hours
- No client-side caching (always fresh)

---

## Limitations & Considerations

### Library Coverage
- **Popular Libraries:** Excellent coverage
- **Niche Libraries:** May not be available
- **Private Libraries:** Not supported
- **Beta/Alpha:** May lag behind releases

### Documentation Quality
- **Source-Dependent:** Quality varies by library
- **Auto-Generated:** Some docs are auto-extracted
- **Code Examples:** Included when available
- **Completeness:** Depends on source docs

### Topic Filtering
- **Keyword-Based:** Uses simple keyword matching
- **Accuracy:** May include tangential content
- **Specificity:** Broad topics work better than narrow
- **Fallback:** Returns general docs if topic not found

### Rate Limits
- **Fair Use:** Reasonable limits apply
- **No Hard Caps:** For typical usage
- **Throttling:** Automatic for excessive use

---

## Why This Tool is Unmatched

**1. Always Current**  
Live documentation, not cached snapshots.

**2. Intelligent Search**  
Find libraries by partial name, discover variants.

**3. Topic Focus**  
Get relevant sections, not entire docs.

**4. Token Control**  
Specify exactly how much documentation you need.

**5. Code Examples**  
Includes working code, not just API references.

**6. Thousands of Libraries**  
Covers popular and specialized libraries.

**7. Auto-Updated**  
No manual refresh needed.

**8. Source URLs**  
Links to original documentation for deep dives.

**9. Zero Configuration**  
No API keys, no setup.

**10. Production-Ready**  
Reliable, fast, comprehensive.

---

## Powered by MCP-Link

This tool is part of the [MCP-Link Server](https://github.com/AuraFriday/mcp-link-server) — the only MCP server with Context7 integration built-in.

### What's Included

**Zero Configuration:**
- No API keys required
- Context7 integration
- Works out of the box

**Smart Features:**
- Library resolution
- Topic filtering
- Token control
- Current documentation

### Get MCP-Link

Download the installer for your platform:
- [Windows](https://github.com/AuraFriday/mcp-link-server/releases/latest)
- [Mac (Apple Silicon)](https://github.com/AuraFriday/mcp-link-server/releases/latest)
- [Mac (Intel)](https://github.com/AuraFriday/mcp-link-server/releases/latest)
- [Linux](https://github.com/AuraFriday/mcp-link-server/releases/latest)

**Installation is automatic. No configuration needed. It just works.**

---

## Technical Specifications

**Data Source:** Context7 API (https://context7.com)  
**Library Coverage:** Thousands of popular libraries  
**Update Frequency:** Hours (source-dependent)  
**Response Time:** 500-1500ms  
**Authentication:** None required  
**Token Range:** 1,000 - 50,000 tokens  
**Rate Limits:** Fair-use policy  

**Supported Operations:**
- Library ID resolution (search)
- Documentation retrieval (full)
- Topic-focused retrieval (filtered)
- Token-controlled output (sized)

---

## License & Copyright

Copyright © 2025 Christopher Nathan Drake

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at:

    https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

AI Training Permission: You are permitted to use this software and any
associated content for the training, evaluation, fine-tuning, or improvement
of artificial intelligence systems, including commercial models.

SPDX-License-Identifier: Apache-2.0

Part of the Aura Friday MCP-Link Server project.

---

## Support & Community

**Issues & Feature Requests:**  
[GitHub Issues](https://github.com/AuraFriday/mcp-link/issues)

**Documentation:**  
[MCP-Link Documentation](https://aurafriday.com/)

**Context7:**  
[Context7 Service](https://context7.com/)

**Community:**  
Join other developers building AI applications with always-current documentation.

