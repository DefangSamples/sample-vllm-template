# Mistral & vLLM

[![1-click-deploy](https://raw.githubusercontent.com/DefangLabs/defang-assets/main/Logos/Buttons/SVG/deploy-with-defang.svg)](https://portal.defang.dev/redirect?url=https%3A%2F%2Fgithub.com%2Fnew%3Ftemplate_name%3Dsample-vllm-template%26template_owner%3DDefangSamples)

This guide demonstrates how to deploy Mistral using vLLM. You'll need a Hugging Face token to begin.

## Prerequisites

- Hugging Face token

## Steps

1. **Set the Hugging Face Token**

   First, set the Hugging Face token using the `defang config` command.

   ```bash
   defang config set --name HF_TOKEN
   ```

2. **Launch with Defang Compose**

   Run the following command to start the services:

   ```bash
   defang compose up
   ```

   The provided `compose.yaml` file includes the Mistral service. It's configured to run on an AWS instance with GPU support. The file also includes a UI service built with Next.js, utilizing Vercel's AI SDK.

   > **OpenAI SDK:** We use the OpenAI sdk, but set the `baseURL` to our Mistral endpoint.

   > **Note:** The API route does not use a system prompt, as the Mistral model we're deploying currently does not support this feature. To get around this we inject a couple messages at the front of the conversation providing the context (see the `ui/src/app/api/chat/route.ts` file). Other than that, the integration with the OpenAI SDK should be structured as expected.

   > **Changing the content:** The content for the bot is set in the `ui/src/app/api/chat/route.ts` file. You can edit the prompt in there to change the behaviour. You'll notice that it also pulls from `ui/src/app/docs.md` to provide content for the bot to use. You can edit this file to change its "knowledge".

## Configuration

- The Docker Compose file is ready to deploy Mistral and the UI service.
- The UI uses Next.js and Vercel's AI SDK for seamless integration.

By following these steps, you should be able to deploy Mistral along with a custom UI on AWS, using GPU capabilities for enhanced performance.

---

Title: Mistral & vLLM

Short Description: Deploy Mistral with a custom UI using vLLM.

Tags: Mistral, vLLM, AI, Nextjs, GPU, Node.js, TypeScript, JavaScript

Languages: nodejs
