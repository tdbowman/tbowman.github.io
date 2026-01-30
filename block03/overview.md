# Block 3: Systems, APIs, AI & Object Thinking

**Duration:** Weeks 8-11
**Core Question:** *How do programs interact with other systems and make decisions?*

---

## 🎯 Block Themes

This block takes you beyond standalone programs. You'll learn to integrate with external systems, work with web APIs, manage databases, and understand object-oriented programming.

Modern software doesn't exist in isolation—it connects to databases, APIs, cloud services, and AI models. Block 3 teaches you to build programs that interact with the wider world of software systems.

---

## 📚 What You'll Learn

### Core Competencies
- **Modular thinking** - Design systems as connected components
- **System integration** - Connect to databases, APIs, and services
- **"Black box" literacy** - Use AI and external systems without understanding internals
- **Data persistence** - Store and retrieve information
- **Network communication** - Fetch and send data over the internet

### Technical Skills
✅ Modules and code organization  
✅ File I/O (reading and writing)  
✅ CSV file processing  
✅ HTTP requests and web APIs  
✅ JSON parsing and generation  
✅ SQL and PostgreSQL databases  
✅ Object-Oriented Programming (OOP)  
✅ Classes and inheritance  

---

## 📅 Weekly Topics

### [Week 8: Modules](../week08/overview.md)
- What are modules and why use them?
- Importing from Python's standard library
- Creating your own modules
- Organizing code across files
- Package structure

**Key Concept:** Modules organize code and enable reuse

### [Week 9: Files](../week09/overview.md)
- Opening, reading, and writing files
- File modes (`r`, `w`, `a`)
- The `with` statement
- CSV file processing
- Error handling for file operations

**Key Concept:** Files persist data beyond program execution

### [Week 10: Internet Data & APIs](../week10/overview.md)
- What are APIs?
- Making HTTP requests with `requests` library
- Parsing JSON responses
- Working with real web APIs
- Error handling and rate limits

**Key Concept:** APIs let programs talk to other programs

### [Week 11: JSON, SQL & PostgreSQL](../week11/overview.md)
- Working with JSON in Python
- Connecting to PostgreSQL databases
- Executing SQL queries from Python
- Safe parameterized queries
- Storing and retrieving structured data

**Key Concept:** Databases manage data at scale

---

## 📝 Assignments in This Block

### Programming Assignments
- **Assignment 2**
  - Work with files and structured data
  - Apply modules and organization

- **Assignment 3**
  - Work with APIs or databases
  - Integrate external data sources
  - Build a complete data pipeline

### Personal Reflections
- **Reflection #2** - AI and automation
- **Reflection #3** - Data ethics and privacy
- **Reflection #4** - System integration challenges

### Group Project
- Continue working on group project
- Apply APIs or databases to project
- Prepare for final presentation

---

## 🎯 Skills You'll Lock In

By the end of Block 3, you will be able to:

### Modular Thinking
- Break programs into logical components
- Design reusable modules
- Organize code across multiple files
- Import and use external libraries

### System Integration
- Connect to web APIs
- Query databases
- Read and write files
- Handle network errors gracefully

### Data Fluency
- Parse JSON from APIs
- Execute SQL queries
- Transform data between formats
- Validate and clean external data

### Object-Oriented Design
- Create classes and objects
- Use inheritance to reuse code
- Design systems with OOP principles
- Understand when OOP is appropriate

---

## 🌟 Why This Block Matters

**Block 3 makes you a systems thinker.** Modern applications are systems of systems:

### Real-World Context

**Web Applications:**
- Frontend ↔ API ↔ Database
- User interface talks to backend via API
- Backend queries database for data

**Data Pipelines:**
- API → JSON → Processing → Database → Reports
- Fetch data, transform it, store it, analyze it

**AI Applications:**
- Data → Model → Predictions → Action
- Feed data to models, get predictions back

### Building on Blocks 1-2
- **Block 1:** You learned to write code
- **Block 2:** You learned to work with data
- **Block 3:** You learn to connect systems

### Preparing for Block 4
Block 4 applies everything to robotics simulation:
- OOP to design robot classes
- File I/O to log robot actions
- System thinking to control virtual robots

---

## 💡 Tips for Success

### Week by Week Strategy

**Week 8:** Organize your code from the start—good habits matter  
**Week 9:** Always use `with` for file operations—safer and cleaner  
**Week 10:** Test with small API calls first—understand before scaling  
**Week 11:** Practice SQL separately—it's a different language  

### Study Habits
1. **Build small projects** - Weather app, news aggregator, data logger
2. **Read documentation** - APIs and libraries have great docs
3. **Handle errors** - Always use try/except for external systems
4. **Test incrementally** - Don't write 100 lines before testing
5. **Learn patterns** - Most API/database code follows templates

### Common Patterns to Master

**API Request Pattern:**
```python
import requests

response = requests.get(url, params=params)
if response.ok:
    data = response.json()
    # Process data
else:
    print(f"Error: {response.status_code}")
```

**Database Query Pattern:**
```python
with psycopg2.connect(**conn_params) as conn:
    with conn.cursor() as cursor:
        cursor.execute("SELECT * FROM table WHERE condition")
        results = cursor.fetchall()
        # Process results
```

**File I/O Pattern:**
```python
with open("file.txt", "r") as f:
    data = f.read()
    # Process data
```

**OOP Pattern:**
```python
class Robot:
    def __init__(self, name):
        self.name = name
    
    def move(self):
        # Movement logic
        pass
```

---

## 🔒 Important Concepts

### API Best Practices
- **Rate limiting** - Don't make too many requests
- **API keys** - Keep them secret, never commit to Git
- **Error handling** - Networks fail, handle it gracefully
- **Caching** - Don't re-fetch the same data

### Database Best Practices
- **Parameterized queries** - Prevent SQL injection
- **Connection management** - Always close connections
- **Transactions** - Group related operations
- **Backups** - Data loss is permanent

### Security Awareness
- Never hardcode passwords
- Use environment variables for secrets
- Validate all external input
- Handle errors without exposing sensitive info

---

## 🚀 Getting Started

**Continue from Block 2:** [Week 8: Modules](../week08/overview.md)

**Or review:** [Block 2: Data Structures](../block02/overview.md)

---

## 📊 Block Structure

```
Block 3: Systems, APIs, AI & Object Thinking
├── Week 8: Modules
├── Week 9: Files
├── Week 10: Internet Data & APIs
└── Week 11: JSON, SQL & PostgreSQL

Previous: Block 2 ← Data Structures
Next: Block 4 → Python + Robotics
```

---

## 🎓 Graduate Students (LIS 805)

Block 3 is where graduate work differentiates:

**Additional Requirements:**
- Deeper theoretical understanding of system architecture
- More complex integrations (multiple APIs, databases)
- Critical analysis of AI systems and bias
- Advanced error handling and edge cases
- Documentation and testing standards

**Reflections:**
- Analyze AI systems you use daily
- Evaluate data privacy implications
- Critique automation and its impacts
- Connect to information science theory

---

**Remember:** You're not just learning APIs and databases—you're learning to think about programs as part of larger ecosystems.

**Ready to integrate systems?** Let's connect! 🌐
