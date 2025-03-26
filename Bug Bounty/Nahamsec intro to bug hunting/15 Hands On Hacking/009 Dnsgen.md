
DNSgen: https://github.com/AlephNullSK/dnsgen

==DNS gen comes with a default wordlist if you dont have any for permutaions==
# DNSGen 2.0 - Advanced DNS Name Permutation Engine 🚀

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

DNSGen is a powerful and flexible DNS name permutation tool designed for security researchers and penetration testers. It generates intelligent domain name variations to assist in subdomain discovery and security assessments.

![DNSGen Banner](https://0xpatrik.com/content/images/2019/09/dnsgen-1.png)

## ✨ Features

- 🔍 Smart domain name permutation engine
- 🚄 Fast generation mode for quick assessments
- 📝 Support for custom wordlists with comments
- 🎯 Intelligent word extraction from existing domains
- 🔧 Multiple permutation techniques
- 🌍 Cloud-aware patterns and modern naming conventions

## 🚀 Quick Start

### Installation

```bash
# Using pip
python -m pip install dnsgen

# Using uv (recommended for development)
git clone https://github.com/AlephNullSK/dnsgen
cd dnsgen/
python -m pip install uv
uv sync
```

### Basic Usage

```bash
# Basic domain permutation
dnsgen domains.txt

# With custom wordlist and output file
dnsgen -w custom_wordlist.txt -o results.txt domains.txt

# Using fast mode for quick assessment
dnsgen -f domains.txt

# Pipe with massdns for resolution
cat domains.txt | dnsgen - | massdns -r resolvers.txt -t A -o J --flush 2>/dev/null
```

## 🛠️ Permutation Techniques

DNSGen 2.0 implements multiple sophisticated permutation techniques:

### Core Permutators

1. **Word Insertion** 
   - Inserts words between domain levels
   - Example: `api.example.com` → `staging.api.example.com`

2. **Number Manipulation**
   - Intelligently modifies existing numbers
   - Example: `api2.example.com` → `api1.example.com`, `api3.example.com`

3. **Word Affixing**
   - Prepends/appends words to levels
   - Example: `api.example.com` → `devapi.example.com`, `api-dev.example.com`

### Cloud & Modern Infrastructure Permutators

4. **Cloud Provider Patterns**
   - Adds cloud-specific naming patterns
   - Example: `example.com` → `api-aws.example.com`, `storage-azure.example.com`

5. **Region Prefixes**
   - Adds geographical region patterns
   - Example: `api.example.com` → `us-east.api.example.com`

6. **Microservice Patterns**
   - Generates microservice-style names
   - Example: `example.com` → `auth-service.example.com`, `user-api.example.com`

### DevOps & Tooling Permutators

7. **Internal Tooling**
   - Adds common internal tool subdomains
   - Example: `example.com` → `jenkins.internal.example.com`

8. **Port Prefixing**
   - Adds common port numbers
   - Example: `api.example.com` → `8080.api.example.com`

## 📋 Command Line Options

```bash
dnsgen [OPTIONS] FILENAME

Options:
  -l, --wordlen INTEGER  Min length of custom words (default: 6)
  -w, --wordlist PATH    Path to custom wordlist
  -f, --fast            Fast generation mode
  -o, --output PATH     Output file path
  -v, --verbose         Enable verbose logging
  --help               Show this message and exit
```

## 🔧 Advanced Usage

### Custom Wordlists

DNSGen 2.0 supports commented wordlists for better organization:

```text
# Environment Names
dev
staging
prod

# Cloud Providers
aws
azure
gcp

# Tools and Services
jenkins
gitlab
grafana
```

### Integration with MassDNS

Get clean resolved domains:
```bash
# Generate and resolve
dnsgen hosts.txt > wordlist.txt
massdns -r resolvers.txt -o S wordlist.txt | grep -e ' A ' | \
  cut -d 'A' -f 1 | rev | cut -d "." -f1 --complement | \
  rev | sort | uniq > resolved_domains.txt
```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for more details.

## 📚 Resources

- [Subdomain Enumeration: 2019 Workflow](https://0xpatrik.com/subdomain-enumeration-2019/)
- [Subdomain Enumeration: Doing it a Bit Smarter](https://0xpatrik.com/subdomain-enumeration-smarter/)
- [Project Documentation](docs/README.md)

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Original concept by [Aleph Null s.r.o.](https://alephnull.sk)
- Inspired by [altdns](https://github.com/infosec-au/altdns)
- [massdns](https://github.com/blechschmidt/massdns) for DNS resolution

## 📊 Project Status

- ✅ Core functionality complete
- 🏗️ Adding more permutation techniques
- 📝 Improving documentation
- 🧪 Adding tests

---

<p align="center">Made with ❤️ by the security community</p>


---




# Transcript :
1
00:00:00,750 --> 00:00:08,160
I like to usually use as DNS, DNS, Djenne allows you to generate their phone permutation of a same

2
00:00:08,160 --> 00:00:08,590
website.

3
00:00:08,670 --> 00:00:13,680
What it does is it will take a number of keywords from you and it will throw it in the subdomains.

4
00:00:13,860 --> 00:00:19,020
For example, in this case, we're using partner mail, Cyclopes courtyard, dot com, and it's taking

5
00:00:19,020 --> 00:00:21,060
those keywords backstage pass.

6
00:00:21,750 --> 00:00:27,600
And you can see that it's adding somewhere in here and it's looking to see if it's other permutations

7
00:00:27,600 --> 00:00:28,010
exist.

8
00:00:28,110 --> 00:00:33,150
So for another example, to make it very simple, as if I'm looking at Melda Yahoo dot com, can I find

9
00:00:33,150 --> 00:00:39,780
Mel Deve, Mel Dash Dev and that sort of other permutations or environments that the developers may

10
00:00:39,780 --> 00:00:42,740
be using to extend our attack surface.

11
00:00:43,050 --> 00:00:44,610
So let's look at installing this.

12
00:00:45,000 --> 00:00:46,710
It looks like it's a super simple install.

13
00:00:46,710 --> 00:00:48,400
All you have to do is use three.

14
00:00:48,730 --> 00:00:50,490
So we're going to go ahead and type that in.

15
00:00:52,590 --> 00:00:54,650
And this is going to insult the nation for us.

16
00:00:54,700 --> 00:00:58,250
I'm going to give it a sec and once it's done, we're going to give it a try.