# Contributing to Lybic Skills

Thank you for your interest in contributing to Lybic Skills!

## How to Contribute

### Reporting Issues

If you find a bug or have a feature request:
1. Check if the issue already exists
2. Create a new issue with:
   - Clear description
   - Steps to reproduce (for bugs)
   - Expected vs actual behavior
   - Your environment (OS, Python version, lybic SDK version)

### Submitting Code

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Test your changes thoroughly
5. Commit with clear messages (`git commit -m 'Add amazing feature'`)
6. Push to your branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

### Code Style

- Follow PEP 8 for Python code
- Use meaningful variable and function names
- Add docstrings to functions and classes
- Include type hints where appropriate
- Keep functions focused and small

### Adding Examples

When adding new examples:
1. Place them in `lybic-skill/examples/`
2. Name files descriptively (e.g., `XX_description.py`)
3. Include a docstring explaining what the example demonstrates
4. Update `examples/README.md` with the new example
5. Test the example thoroughly

### Documentation

- Keep documentation clear and concise
- Use code examples liberally
- Update relevant docs when changing functionality
- Check for spelling and grammar

## Development Setup

```bash
# Clone your fork
git clone https://github.com/lybic/skills.git
cd lybic-skills

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install lybic

# Set up credentials
export LYBIC_ORG_ID="your_org_id"
export LYBIC_API_KEY="your_api_key"

# Test examples
cd lybic-skill/examples
python 01_execute_code.py
```

## Testing

Before submitting:
1. Test your code with actual Lybic sandboxes
2. Verify all examples run without errors
3. Check that documentation is accurate
4. Ensure no credentials are committed

## Questions?

Feel free to open an issue for:
- Questions about contribution process
- Clarification on features
- Discussion of proposed changes

Thank you for contributing! 🎉
