# EGAF CLI Quick Reference Guide

<style>
body {
    background-color: #0a0b0e;
    color: #e4e4e4;
}

.container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

.section {
    background: linear-gradient(145deg, #1a1d21 0%, #13151a 100%);
    border: 1px solid #2a2f3a;
    border-radius: 12px;
    padding: 20px;
    margin: 10px 0;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    backdrop-filter: blur(10px);
    transition: all 0.3s ease;
}

.section:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(74, 158, 255, 0.15);
    border-color: #4a9eff;
}

.section.full-width {
    grid-column: 1 / -1;
}

.command {
    background: linear-gradient(90deg, #1e222a 0%, #282c34 100%);
    color: #e4e4e4;
    padding: 12px 16px;
    border-radius: 8px;
    font-family: 'JetBrains Mono', monospace;
    margin: 8px 0;
    border: 1px solid #3a3f4b;
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);
}

.title {
    background: linear-gradient(90deg, #4a9eff 0%, #3178c6 100%);
    color: white;
    padding: 12px 16px;
    border-radius: 8px;
    margin-bottom: 15px;
    font-weight: bold;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    box-shadow: 0 2px 8px rgba(74, 158, 255, 0.2);
    display: flex;
    align-items: center;
    gap: 8px;
}

pre {
    margin: 8px 0;
    white-space: pre-wrap;
}

.option {
    color: #4a9eff;
    text-shadow: 0 0 8px rgba(74, 158, 255, 0.3);
}

.param {
    color: #98c379;
    text-shadow: 0 0 8px rgba(152, 195, 121, 0.3);
}

h3 {
    color: #4a9eff;
    margin: 15px 0 10px;
    font-size: 1.1em;
    text-shadow: 0 0 8px rgba(74, 158, 255, 0.2);
}

code {
    color: #e4e4e4;
    background-color: #2a2f3a;
    padding: 2px 6px;
    border-radius: 4px;
    font-family: 'JetBrains Mono', monospace;
}

ul, ol {
    padding-left: 20px;
    margin: 8px 0;
}

li {
    margin: 4px 0;
    color: #b4b4b4;
}

li code {
    color: #4a9eff;
}

/* Glowing effect for emojis */
.title span {
    font-size: 1.2em;
    filter: drop-shadow(0 0 8px rgba(74, 158, 255, 0.4));
}
</style>

<div class="container">

<div class="section">
<div class="title"><span>🆕</span> Create New Projects</div>

```bash
egaf new <template> --name <project-name> --lang <language> --company <company>
```

### Templates
- 📦 `guidance` - .NET Guidance-style project
- 🔧 `microservice` - Java microservice
- 🐍 `fastapi` - Python FastAPI project

### Common Options
- `--name, -n` : Project name
- `--lang, -l` : Language (dotnet|java|python)
- `--company, -c` : Company (Elia|50Hertz)
</div>

<div class="section">
<div class="title"><span>⚙️</span> Configuration</div>

```bash
# Set Global Config
egaf config set --company <company> \
    --lang <lang> \
    --username <user> \
    --email <email>
```

### Options
- `--company, -c` : Company name
- `--lang, -l` : Programming language
- `--username, -u` : User name
- `--email, -e` : Company email
</div>

<div class="section">
<div class="title"><span>➕</span> Database Features</div>

```bash
# Add MSSQL Support
egaf add mssql -n <name> -m <microservice> -d <database>

# Add MongoDB Support
egaf add mongodb -m <microservice> [--name <name>]
```

### Common Options
- `-n, --name` : Project name
- `-m, --microservice` : Target microservice
- `-d, --database` : Database name
- `-s, --server` : Server name (optional)
</div>

<div class="section">
<div class="title"><span>🔌</span> API Features</div>

```bash
# Add REST API
egaf add rest --layer <facade|interface> \
    -m <microservice> -n <name>

# Add gRPC Service
egaf add grpc --layer <facade|interface> \
    -m <microservice> -n <name>
```

### API Layers
- `facade` - For external APIs
- `interface` - For internal services
</div>

<div class="section">
<div class="title"><span>📊</span> Entity Management</div>

```bash
# Add Entity
egaf add entity -n <name> -t <type> -m <microservice>
```

### Entity Types
- `Entity` - Basic entity
- `Audit` - With audit properties
- `Create` - With creation tracking
- `Update` - With update tracking
- `Delete` - With deletion tracking
</div>

<div class="section">
<div class="title"><span>⚡</span> Jobs & Tasks</div>

```bash
# Add Hangfire Jobs
egaf add jobs -m <microservice> \
    -db <database> -s <server>
```

### Options
- `-m, --microservice` : Target microservice
- `-db, --database` : Hangfire database
- `-s, --server` : Database server
</div>

<div class="section full-width">
<div class="title"><span>📝</span> Quick Examples</div>

```bash
# Create new .NET project
egaf new guidance -n MyService -l dotnet -c Elia

# Add database to microservice
egaf add mssql -n Persistence -m Core -d MyDb

# Add REST API with facade layer
egaf add rest --layer facade -m Core -n MyEntity
```
</div>

<div class="section full-width">
<div class="title"><span>💡</span> Tips & Notes</div>

- Use `--help` with any command for detailed options
- Version info available with `--version`
- Config settings are stored in `~/.config/egaf/egaf.json`
- Most commands require being in project directory
- Use tab completion for faster command typing
- Commands can be chained for multiple operations
</div>

</div> 
