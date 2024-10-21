# Cloudflare MTA-STS policy via static assets

This is a simple example how to serve MTA-STS policy file

```
.well-known/mta-sts.txt
```

as a static Cloudflare asset for multiple domains. Static only assets do not count against your Wokers usage, they are completely free.

Static assets are a new Cloudflare feature, see [documentation](https://developers.cloudflare.com/workers/static-assets/)

## Prerequisites

- [Node.js](https://nodejs.org/) (version 18 or later)
- [Wrangler CLI](https://developers.cloudflare.com/workers/cli-wrangler/install-update) (version 3 or later)
- A Cloudflare account with Workers enabled

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/fry69/cloudflare-mta-sts-static.git
   cd cloudflare-mta-sts-static
   ```

2. Install dependencies:
   ```
   npm install
   ```

3. Configure your Cloudflare account in Wrangler:
   ```
   wrangler login
   ```

4. Optionally update the `wrangler.toml` file with your custom domains:
   ```
   routes = [
     { pattern = "mta-sts.example1.com", custom_domain = true },
     { pattern = "mta-sts.example2.com", custom_domain = true }
   ]
   ```

## Usage

1. Develop and test locally:
   ```
   npm run dev
   ```

2. Deploy to Cloudflare Workers:
   ```
   npm run deploy
   ```

3. Add a custom domain in your Cloudflare dashboard to direct traffic to this asset only worker or add custom domains in `wrangler.toml` as described above.

## Customization

Edit the policy file in

```
public/.well-known/mta-sts.txt
```

conforming to [RFC 8641](https://datatracker.ietf.org/doc/html/rfc8461)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Cloudflare Workers](https://workers.cloudflare.com/) for the serverless platform

## Support

If you encounter any problems or have any questions, please open an issue in this repository.
