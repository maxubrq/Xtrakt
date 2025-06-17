# Xtrakt

**Xtrakt** is a fast and reliable archive extraction engine written in Rust. It supports popular compression formats like ZIP, RAR, and 7z, offering both CLI and library interfaces for seamless integration into your workflows.

## 🎯 Features

- 📦 Supports common archive formats: `.zip`, `.rar`, `.7z`, `.tar.gz`, and more
- 🚀 High performance with memory-safe concurrency (thanks to Rust)
- 📁 Recursive extraction (archives within archives)
- 🔐 Optional password support (for protected archives)
- 🧰 CLI & API access – scriptable or embeddable
- 🧼 Safe extraction: avoids zip-slip and related security risks

---

## 📦 Installation

### From Source

```bash
git clone https://github.com/your-org/xtrakt.git
cd xtrakt
cargo build --release
````

> Requires Rust 1.70+ and `cargo`.

---

## 🛠️ Usage

### CLI Example

```bash
xtrakt extract archive.zip --output ./output_dir
```

With password:

```bash
xtrakt extract secure.7z --output ./out --password "s3cr3t"
```

Recursive:

```bash
xtrakt extract nested.zip --output ./out --recursive
```

### Rust Library API

```rust
use xtrakt::extractor::Extractor;

fn main() {
    let archive_path = "path/to/archive.7z";
    let output_path = "output/";
    
    let extractor = Extractor::new();
    extractor.extract(archive_path, output_path).unwrap();
}
```

---

## 📁 Supported Formats

| Format    | Read | Write | Password-Protected |
| --------- | ---- | ----- | ------------------ |
| `.zip`    | ✅    | ❌     | ✅ (planned)        |
| `.rar`    | ✅    | ❌     | ✅ (limited)        |
| `.7z`     | ✅    | ❌     | ✅                  |
| `.tar`    | ✅    | ❌     | ❌                  |
| `.tar.gz` | ✅    | ❌     | ❌                  |

> Format support depends on available crates and native bindings. Some formats may require external binaries (like `7z` or `unrar`).

---

## 🔐 Security

* Prevents directory traversal attacks (e.g., `../../evil.sh`)
* Optional sandboxing support (planned)
* Robust error handling for corrupted or malformed archives

---

## 📚 Documentation

Coming soon on [docs.rs/xtrakt](https://docs.rs/xtrakt)

---

## 🔧 Project Structure

```
xtrakt/
├── src/
│   ├── cli.rs          # CLI parsing
│   ├── extractor.rs    # Core logic for archive extraction
│   ├── formats/        # Format-specific handlers
│   └── lib.rs
├── examples/
├── tests/
└── Cargo.toml
```

---

## 🧪 Running Tests

```bash
cargo test
```

---

## 🤝 Contributing

Pull requests and feature suggestions are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md).

---

## 📄 License

MIT License. See [LICENSE](LICENSE) for details.

---

Made with 🦀 by \[Your Name / Org]
