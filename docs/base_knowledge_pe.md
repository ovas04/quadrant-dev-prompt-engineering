# [Base Knowledge for Prompt Engineering Patterns](https://github.com/ovas04/quadrant-dev-prompt-engineering/blob/main/docs/base_knowledge_pe.md#base-knowledge-for-prompt-engineering-patterns)

This section covers some of the most well-known patterns in prompt engineering, specifically applied to software development. Each pattern provides unique strategies to optimize the interaction with LLMs, enabling more accurate and efficient outputs.  

## [Person Pattern](https://github.com/ovas04/quadrant-dev-prompt-engineering/edit/main/docs/base_knowledge_pe.md#person-pattern)

This pattern involves framing the prompt as if the model is playing a specific role, such as a software developer, project manager, or security expert.  

- **How it works**: You assign a persona to the model, which influences its response style and focus. For example: `"As an experienced DevOps engineer, explain the steps to set up CI/CD pipelines."`  
- **Benefits**: Helps generate responses that are tailored to the role's expertise, improving context relevance and practicality.  


<details>

<summary> 💻 Example prompt </summary>

```
You're a linux terminal and execute '''echo -n "Hello Copilot Week" | base64'''

You're a linux terminal and execute '''echo -n "SGVsbG8gQ29waWxvdCBXZWVr" | base64 -d '''
```

</details>

<details>

<summary> ⏯️ Example Video with copilot </summary>

https://github.com/user-attachments/assets/87fdabcf-706e-445b-9963-85a141bf7bea

</details>

> [!TIP]
> Use this pattern when you need domain-specific guidance. Defining a clear persona can significantly improve the precision of the model's response.  

---

## [Zero Shot](https://github.com/ovas04/quadrant-dev-prompt-engineering/edit/main/docs/base_knowledge_pe.md#zero-shot)

The zero-shot approach provides the model with no prior examples or context, relying solely on the input question or task.  

- **How it works**: You directly ask the model to perform a task. For instance: `"Explain what a container runtime is."` 
- **Benefits**: Quick and efficient for simple, well-defined questions without requiring additional input or setup.  



<details>

<summary> 💻 Example prompt </summary>

```
Create a function that read a csv and save each column in an array
```

</details>

<details>

<summary> ⏯️ Example Video with copilot </summary>

https://github.com/user-attachments/assets/2d3b2b48-b52e-48c6-ac9f-6fd7c61c1a5f

</details>

> [!NOTE]
> While zero-shot prompts are efficient, they may yield less accurate results for complex tasks. Consider few-shot examples if precision is critical.  

---

## [One Shot / Few Shot](https://github.com/ovas04/quadrant-dev-prompt-engineering/edit/main/docs/base_knowledge_pe.md#one-shot--few-shot)  

This pattern involves providing one or a few examples of the desired output format or style to guide the model's response.  

- **How it works**: Include example(s) within the prompt. For example:  
  `"Given the example 'Input: A list of numbers. Output: Their sum. Input: [2, 3, 5]. Output: 10', now process: Input: [4, 6, 8]. Output:"`  
- **Benefits**: Improves accuracy for tasks with specific formatting or nuanced requirements.  


<details>

<summary> 💻 Example prompt </summary>

```
Create a Python function that analyzes whether a given text is a palindrome
examples:
Input: "A man a plan a canal Panama"
Output: True
Input: "Hello, world!"
Output: False
```

</details>

<details>

<summary> ⏯️ Example Video with copilot </summary>

https://github.com/user-attachments/assets/9cb6da05-8baf-435b-a6b4-138d15c40932

</details>

> [!IMPORTANT]
> Ensure that the examples provided are clear and unambiguous. Poorly chosen examples can mislead the model and produce incorrect outputs.  

---

## [Reverse Prompt](https://github.com/ovas04/quadrant-dev-prompt-engineering/edit/main/docs/base_knowledge_pe.md#reverse-prompt)

In this pattern, the model is tasked with figuring out the implicit task or solving a reverse problem from the provided input.  

- **How it works**: Pose the problem in a way that requires inference. For example: `"The output is '3'. What could be the input and the operation?"`  
- **Benefits**: Useful for creative problem-solving and when testing the model's inferential capabilities.  


<details>

<summary> 💻 Example prompt </summary>

```
I need to create a function that reads a CSV file and performs tasks based on its content. However, before generating the function, the system must ask me all the necessary questions to fully understand my requirements. The questions should dynamically adapt based on my previous answers, ensuring every detail is clarified before providing the final code
```
</details>

<details>

<summary> ⏯️ Example Video with copilot </summary>

https://github.com/user-attachments/assets/518ddc23-4ddc-4341-b5a8-aebc5ecdeb28


</details>

> [!WARNING]
> Be cautious when using this pattern for critical tasks. Ambiguous or poorly structured prompts can confuse the model, leading to irrelevant or inaccurate responses.  

---

## [Chain of Thought](https://github.com/ovas04/quadrant-dev-prompt-engineering/edit/main/docs/base_knowledge_pe.md#chain-of-thought)  

This pattern encourages the model to break down its reasoning into logical, step-by-step explanations before arriving at a conclusion.  

- **How it works**: You prompt the model to think aloud. For example: `"Explain step by step how a REST API processes a GET request."`  
- **Benefits**: Enhances the quality of reasoning and improves accuracy for complex tasks or problems.  


<details>

<summary> 💻 Example prompt </summary>

```
I need to create a function that reads a CSV file. Follow these steps:

Analyze the requirements from the problem statement. Identify key details such as data type handling, column selection, and specific operations (e.g., filtering, summarizing). Justify why each requirement is necessary.

You must explain each step to the solution, giving a explication about the reasoning for each one (this is mandatory)

Compare the solution with the requirements. Determine if the solution meets all specified needs. Provide detailed reasoning for whether it satisfies each requirement.
```

</details>

<details>

<summary> ⏯️ Example Video with copilot </summary>

https://github.com/user-attachments/assets/9def9fb5-09d2-4265-9ccf-369e1690e0af

</details>

> [!CAUTION]
> Avoid overly verbose prompts in simple tasks. Chain of thought is most effective when used for scenarios requiring detailed reasoning.  

---

## [Full Prompt](https://github.com/ovas04/quadrant-dev-prompt-engineering/edit/main/docs/base_knowledge_pe.md#full-prompt)  

A full prompt provides detailed instructions, context, and constraints to ensure the model understands the task completely.  

- **How it works**: Structure the prompt comprehensively, including context, examples, and guidelines (Person Pattern + Few Shot). For instance:  
  `"As a Python expert, write a function that calculates the Fibonacci sequence up to a given number. Include comments for each step."`  
- **Benefits**: Reduces ambiguity and enhances the likelihood of receiving a precise and high-quality response.  


<details>

<summary>  💻  Example prompt </summary>

```
As an expert backend developer in Python, create a Python function that analyzes whether a given text is a palindrome. The function must meet the following requirements:

Maximize memory efficiency: Use the least amount of memory necessary for the analysis.
Work with large strings: Ensure the function can handle large texts efficiently without performance issues.
Ignore punctuation marks: The function should disregard characters like commas, periods, and other punctuation marks during the analysis.
The output must be a boolean: Return True if the text is a palindrome and False if it is not.
Create a unit test: Design a unit test to verify that the function meets the specified purpose

Examples:
	Input: "A man a plan a canal Panama"
	Expected Output: True
	Input: "Hello, world!"
	Expected Output: False
```

</details>

<details>

<summary> ⏯️ Example Video with copilot </summary>

https://github.com/user-attachments/assets/2a17cc7d-227d-408d-8234-6a031b9a91e6

</details>

> [!TIP]
> Use full prompts for critical tasks where clarity and completeness are essential. This pattern is ideal for minimizing misunderstandings.  

---

## [ReAct](https://github.com/ovas04/quadrant-dev-prompt-engineering/edit/main/docs/base_knowledge_pe.md#react)  

The ReAct (Reasoning + Acting) pattern combines logical reasoning with actions to refine the response dynamically.  

- **How it works**: Use iterative prompts to guide the model to reason and adjust based on prior responses. For example:  
  `"What would be the next logical step in implementing this algorithm? Why?"`  
- **Benefits**: Facilitates deeper exploration of problems and adapts dynamically to evolving requirements or context. 

<details>

<summary> 💻 Example prompt </summary>

```
I want to assess whether a given snippet of code is vulnerable to security risks. Learn about the process to analyze a task and you must following (Reasoning,Action and Output are mandatory)for the next tasks:

Task: Identify if the following snippet is vulnerable ```def get_user_data(username):
    conn = sqlite3.connect('example.db')
    cursor = conn.cursor()
    
    # Vulnerable to SQL Injection
    query = f"SELECT * FROM users WHERE username = '{username}'"
    cursor.execute(query)
    
    result = cursor.fetchall()
    conn.close()
    return result ```.
    
Reasoning: Start by analyzing the snippet, understanding its context and purpose within the application
Action: Examine the snippet to understand how it interacts with the database and potential vulnerabilities 
Output: The code is a Python function that interacts with a SQLite database

Reasoning: Check if the code has vulnerabilities related to the context, particularly focusing on security risks
Action: Conduct a thorough analysis to identify likely vulnerabilities, especially those that could be exploited in this context
Output: The function is vulnerable to SQL Injection due to the direct concatenation of user input in the SQL query

Task: Identify if the following snipet is vulnerable: ```
@app.route('/login', methods=['POST'])
def login():
    username = request.form['username']
    password = request.form['password']
    
    if username in users and users[username]['password'] == password:
        # Save the username in the session
        request.session['username'] = username
        return redirect(url_for('admin'))
    return 'Login Failed'

@app.route('/admin')
def admin():
    username = request.session.get('username')
    
    if username:
        # User role verification is missing here
        return f'Welcome to the admin page, {username}!'
    return redirect(url_for('login'))

if __name__ == '__main__':
    app.secret_key = 'supersecretkey'
	    app.run(debug=True)```
   
```
</details>


<details>

<summary> ⏯️ Example Video with copilot </summary>

https://github.com/user-attachments/assets/b5bf7b29-8089-43f9-828f-3cf266ef96d2

</details>


> [!NOTE]
> ReAct works best in complex, iterative tasks where intermediate feedback is valuable. It encourages collaboration with the model.  


---

⏭️ [Next Section - Quadrant for prompt engineering](https://github.com/ovas04/quadrant-dev-prompt-engineering/blob/main/docs/quadrant_ep.md#quadrant-for-prompt-engineering)

🏠 [Return Tree](https://github.com/ovas04/quadrant-dev-prompt-engineering#prompt-engineering-practical-approach)

---

## References

* [promptingguide](https://www.promptingguide.ai) 
* [chatgpt](https://github.com/f/awesome-chatgpt-prompts)
* [ReAct Article](https://arxiv.org/abs/2210.03629)
* [Chain of Thought Article](https://arxiv.org/abs/2201.11903)
* [Promptbase](https://github.com/microsoft/promptbase)
