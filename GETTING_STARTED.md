# Getting Started with Lybic Skills

This guide will help you get up and running with the lybic-skill quickly.

## What You'll Need

1. **A Lybic Account**
   - Sign up at [dashboard.lybic.cn](https://dashboard.lybic.cn/auth/sign-up)
   - Claim your free trial credits
   - Note your Organization ID and API Key

2. **Python 3.10+**
   ```bash
   python --version  # Should be 3.10 or higher
   ```

3. **The Lybic Python SDK**
   ```bash
   pip install lybic
   ```

## 5-Minute Quickstart

### Step 1: Set Credentials

```bash
export LYBIC_ORG_ID="ORG-your-org-id"
export LYBIC_API_KEY="lysk-your-api-key"
```

> **Where to find these?**
> 1. Log into [Lybic Dashboard](https://dashboard.lybic.cn)
> 2. Go to "Settings" → "API Keys"
> 3. Your Organization ID is shown at the top
> 4. Create an API key if you don't have one

### Step 2: Test Connection

Create a file `test_connection.py`:

```python
import asyncio
from lybic import LybicClient

async def main():
    async with LybicClient() as client:
        stats = await client.stats.get()
        print(f"✓ Connected! You have {stats.sandboxes} sandbox(es)")

asyncio.run(main())
```

Run it:
```bash
python test_connection.py
```

### Step 3: Create Your First Sandbox

```python
import asyncio
from lybic import LybicClient

async def main():
    async with LybicClient() as client:
        # Create sandbox
        print("Creating sandbox...")
        sandbox = await client.sandbox.create(
            name="my-first-sandbox",
            shape="beijing-2c-4g-cpu-linux"
        )
        print(f"✓ Created: {sandbox.id}")
        
        # Take screenshot
        print("Taking screenshot...")
        url, _, _ = await client.sandbox.get_screenshot(sandbox.id)
        print(f"Screenshot: {url}")
        
        # Clean up
        print(f"Deleting sandbox...")
        await client.sandbox.delete(sandbox.id)
        print("✓ Done!")

asyncio.run(main())
```

## What to Try Next

### 1. Run Code in Sandbox

```python
import asyncio
import base64
from lybic import LybicClient

async def main():
    async with LybicClient() as client:
        # Assume you have a sandbox: SBX-xxxx
        sandbox_id = "SBX-xxxx"
        
        code = "print('Hello from cloud!')"
        result = await client.sandbox.execute_process(
            sandbox_id,
            executable="python3",
            stdinBase64=base64.b64encode(code.encode()).decode()
        )
        
        print(base64.b64decode(result.stdoutBase64).decode())

asyncio.run(main())
```

### 2. Automate a GUI

```python
import asyncio
from lybic import LybicClient

async def main():
    async with LybicClient() as client:
        sandbox_id = "SBX-xxxx"
        
        # Click at center
        await client.sandbox.execute_sandbox_action(
            sandbox_id,
            action={
                "type": "mouse:click",
                "x": {"type": "/", "numerator": 500, "denominator": 1000},
                "y": {"type": "/", "numerator": 500, "denominator": 1000},
                "button": 1
            }
        )
        
        # Type text
        await client.sandbox.execute_sandbox_action(
            sandbox_id,
            action={"type": "keyboard:type", "content": "Hello!"}
        )

asyncio.run(main())
```

### 3. Download and Process Files

```python
import asyncio
from lybic import LybicClient
from lybic.dto import FileCopyItem, HttpGetLocation, SandboxFileLocation

async def main():
    async with LybicClient() as client:
        sandbox_id = "SBX-xxxx"
        
        # Download file
        await client.sandbox.copy_files(
            sandbox_id,
            files=[
                FileCopyItem(
                    id="data",
                    src=HttpGetLocation(url="https://example.com/data.csv"),
                    dest=SandboxFileLocation(path="/tmp/data.csv")
                )
            ]
        )
        print("✓ File downloaded!")

asyncio.run(main())
```

## Explore Examples

The repository includes working examples:

```bash
cd lybic-skill/examples
python 01_execute_code.py
```

See [lybic-skill/examples/README.md](lybic-skill/examples/README.md) for all examples.

## Common Patterns

### Pattern: Create, Use, Cleanup

```python
async with LybicClient() as client:
    # Create
    sandbox = await client.sandbox.create(name="temp", shape="beijing-2c-4g-cpu-linux")
    
    try:
        # Use
        # ... do work ...
        
    finally:
        # Cleanup
        await client.sandbox.delete(sandbox.id)
```

### Pattern: Work with Existing Sandbox

```python
async with LybicClient() as client:
    # Get existing sandbox
    sandbox = await client.sandbox.get("SBX-xxxx")
    
    # Work with it
    url, img, _ = await client.sandbox.get_screenshot(sandbox.id)
```

## Troubleshooting

### "Authentication failed"
- Check your `LYBIC_ORG_ID` and `LYBIC_API_KEY`
- Verify they're exported in your current shell
- Try printing them: `echo $LYBIC_ORG_ID`

### "Sandbox not ready"
- Wait longer after creation (try 20-30 seconds)
- Check status: `await client.sandbox.get(sandbox_id)`

### "Module 'lybic' not found"
- Install SDK: `pip install lybic`
- Verify: `pip show lybic`

### "Action failed"
- Take a screenshot first to see current state
- Verify coordinates are within screen bounds
- Ensure action type matches sandbox (desktop vs mobile)

## Best Practices

1. ✅ Always use `async with LybicClient()` for proper cleanup
2. ✅ Wait 10-30s after creating sandbox before interacting
3. ✅ Use fractional coordinates for resolution independence
4. ✅ Delete sandboxes when done to avoid charges
5. ✅ Take screenshots to verify GUI state
6. ✅ Handle errors with try/except
7. ✅ Check exit codes (0 = success)

## Next Steps

- 📖 Read the [full skill documentation](lybic-skill/SKILL.md)
- 📝 Try the [examples](lybic-skill/examples/)
- 🔍 Check the [quick reference](lybic-skill/QUICKREF.md)
- 🌐 Visit [Lybic Documentation](https://docs.lybic.cn)
- 🎮 Try the [Lybic Playground](https://playground.lybic.cn)

## Getting Help

- 💬 Open an [issue](../../issues) for bugs or questions
- 📧 Contact Lybic support at support@lybic.cn
- 📚 Read the [Python SDK docs](https://docs.lybic.cn/en/sdk/python)

Happy coding! 🚀
