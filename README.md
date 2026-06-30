# Use GitHub Copilot with Free Open-Source LLMs

This guide explains how to use **GitHub Copilot Chat** in **Visual Studio Code** with **free NVIDIA-hosted open-source language models** instead of relying on proprietary models. By leveraging NVIDIA's **Build** platform, you can generate a free API key for supported open-source models and connect them directly to GitHub Copilot through a custom endpoint.

At the time of writing, the only limitation I have encountered is a rate limit of approximately **40 requests per minute** on the free endpoints, which is more than sufficient for most development workflows.

---

## Prerequisites

Before getting started, make sure you have:

- A Microsoft account.
- A GitHub account.
- Visual Studio Code installed.
- An internet connection.

---

## Step 1 – Install or Update Visual Studio Code

If you do not already have Visual Studio Code installed, download it from Microsoft's official website:

https://code.visualstudio.com/

If VS Code is already installed, ensure that you are using the latest version.

To check for updates:

1. Open Visual Studio Code.
2. Look at the top title bar.
3. If an **Update** button appears near the top-right area of the window, install the available update before continuing.

> Keeping VS Code up to date ensures compatibility with the latest GitHub Copilot features, including custom language models.

---

## Step 2 – Sign In

Sign in to Visual Studio Code using your Microsoft or GitHub account.

If you do not already have an account, create one before proceeding.

A signed-in account is required in order to use **GitHub Copilot Chat** with custom language models.

---

## Step 3 – Generate a Free NVIDIA API Key

Go to:

https://build.nvidia.com/models

This website provides free API access to many open-source language models.

### Choose a model

Browse the available models and select the one that best fits your needs.

To simplify your search:

- Use the filters in the left sidebar.
- Enable the **Free Endpoints** filter.
- Only select models that provide free endpoints.

Once you have chosen a model:

1. Open its dedicated page.
2. Click **Generate API Key**.

If this is your first time using NVIDIA Build, you will be asked to:

- Create an NVIDIA account.
- Complete a short setup process.
- Create your workspace.

After completing the setup, NVIDIA will display your API key.

It is usually shown inside the variable named:

```text
api_key
```

**Save this value somewhere safe**, such as a password manager or a secure notes application, as you will need it during the next steps.

---

## Step 4 – Add the Model to Visual Studio Code

Open Visual Studio Code.

Open the Command Palette:

**Windows / Linux**

```text
Ctrl + Shift + P
```

**macOS**

```text
Cmd + Shift + P
```

Search for:

```text
Chat: Manage Language Models
```

Then:

1. Click **Add Models**.
2. Select **Custom Endpoint**.
3. Press **Enter** to keep the default name (**Custom Endpoint**).
4. Paste your NVIDIA API key (without quotation marks).

VS Code will then automatically open a JSON configuration file.

---

## Step 5 – Configure the JSON File

Inside the generated JSON file, you only need to modify the following fields:

- `id`
- `name`
- `url`

### `id`

The model identifier can be found on the NVIDIA model page.

Look for the variable named:

```text
model
```

Copy its value exactly.

Example:

```json
"id": "deepseek-ai/deepseek-v4-pro"
```

### `name`

This field is only used for display purposes inside VS Code.

Choose any name you like.

Example:

```json
"name": "DeepSeek V4 Pro"
```

### `url`

For most NVIDIA models, the endpoint is:

```text
https://integrate.api.nvidia.com/v1
```

---

## Step 6 – Start Using Your Model

Open the Command Palette again:

```text
Ctrl + Shift + P
```

(or `Cmd + Shift + P` on macOS)

Search for:

```text
Chat: Open Chat
```

Once the chat window is open:

1. Click the **Auto** model selector.
2. Select **Other Models**.
3. Choose the model you configured.

Your NVIDIA-hosted model should now be available and ready to use inside GitHub Copilot Chat.

---

## Troubleshooting

### My model does not appear

If your model is not listed:

- Close Visual Studio Code completely.
- Reopen it.
- Open the chat again.

VS Code may require a restart before newly added custom models become available.

---

## Notes

- This method relies on NVIDIA Build's free API endpoints.
- Only models marked with **Free Endpoints** can be used without additional cost.
- At the time of writing, the observed limitation is approximately **40 requests per minute**.
- Different models expose different capabilities (context length, tool calling, vision support, etc.). Consult each model's NVIDIA page for details.
