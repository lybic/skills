# Lybic Skills

A collection of Agent Skills for the Lybic cloud sandbox platform.

## What is Lybic?

Lybic (/ˈlaɪbik/) is a powerful cloud-based AI infrastructure platform that provides on-demand sandboxes specifically designed for GUI agent development and execution. It supports Windows, Linux, and Android sandboxes with full GUI interaction capabilities.

## 🚀 Quick Start

```bash
# Install Lybic Python SDK
pip install lybic

# Set credentials
export LYBIC_ORG_ID="your_org_id"
export LYBIC_API_KEY="your_api_key"

# Try an example
cd lybic-skill/examples
python 01_execute_code.py
```

📖 **[Read the Getting Started Guide →](GETTING_STARTED.md)**

## 📦 Skills

### lybic-skill

The main skill that enables AI agents to interact with Lybic cloud sandboxes through the Python SDK.

**Capabilities:**
- ✅ Create and manage cloud sandboxes (Windows/Linux/Android)
- ✅ Execute GUI actions (mouse, keyboard, touch operations)
- ✅ Run code and commands in sandboxes (Python, Node.js, Go, Rust, Java)
- ✅ Transfer files to/from sandboxes
- ✅ Take screenshots and monitor sandbox state
- ✅ Manage HTTP port mappings for web services

**Documentation:**
- [README](./lybic-skill/README.md) - User guide and examples
- [SKILL.md](./lybic-skill/SKILL.md) - AI agent instructions
- [QUICKREF.md](./lybic-skill/QUICKREF.md) - Quick reference
- [Examples](./lybic-skill/examples/) - Working code samples

## 📚 Documentation

- **[Getting Started](GETTING_STARTED.md)** - 5-minute quickstart guide
- **[Contributing](CONTRIBUTING.md)** - How to contribute
- **[Summary](SUMMARY.md)** - Repository overview

## 🎯 Use Cases

This skill is perfect for:
- 🖥️ GUI automation (desktop and mobile apps)
- 🧪 Testing in isolated environments
- 🤖 AI agent development
- 📊 Data processing in cloud sandboxes
- 🌐 Web service testing
- 📱 Android app automation

## 🔗 Links

- [Lybic Dashboard](https://dashboard.lybic.cn)
- [Lybic Documentation](https://docs.lybic.cn)
- [Python SDK Reference](https://docs.lybic.cn/cn/sdk/python)
- [Playground](https://playground.lybic.cn)

## 📄 License

MIT - see [LICENSE](LICENSE) file for details

---

**Made for AI agents and human developers** 🤖 + 👨‍💻
