# Objective-based Autonomous Cognitive Entity (OACE) Framework & the Autonomous AI Developer

## Table of Contents
- [Table of Contents](#table-of-contents)
- [General Introduction](#general-introduction)
- [World / Environment](#world--environment)
- [Abilities](#abilities)
- [Memory](#memory)
- [Layer Processing General](#layer-processing-general)
- [Layer Communication](#layer-communication)
- [Comprehension Layer](#comprehension-layer)
- [Executive Function Layer](#executive-function-layer)
- [Cognitive Control](#cognitive-control)
- [Task Prosecution(s) Layer](#task-prosecutions-layer)
- [Credits \& additional resources](#credits--additional-resources)


## General Introduction 

General Problem with building really capable AI Agents right now:
- GPT-4 is superior to humans https://lifearchitect.ai/iq-testing-ai/. Let GPT-4 operate in the right context and with the given executive abilities and it will be more capable than you, executing your tasks at higher precision. What GPT-4 is missing is an cognitive architecture to make use of its 'intelligence'. 
- Contextualisation is a big problem. An Agent-self´s model, its current objective context, its world context, its project context, its broader context of interaction. The agent has to understand everything from small to big at every step when its needed.
- The agents has to have the abilities to actually interact and implements its work. Iterate on it, now that it created past versions of work.

The core challenges associated with building the Autonomous AI Developer:
- Working with various, vastly different codebases at scale. Being able to comprehend any codebase, any size, any tech stack and find the right, relevant contents to edit at a time. Being able to work in everything from js, ts, python, rust, c++ to cobol and assembly. An agnostic system that can contextualise any codebase. Understand it like a developer, navigate it like a developer.
- Having an actual environment and abilities to write the code, run the code & deployment, navigate the code, navigate logs basically the IDE & Deployment // Dev environment & make sense of them contextually.
- Generating valid code. Actual challenge to generate valid working code is iteration. That said the challenge is creating test methods that can validate if the works correctly, rather than just generating the code. What are the right testing methods to ensure we generate valid code?
- Assembling context in a way that the AI understands what it is, where it is, what it should do next, how it should do it, what it already did. What, Where, Who, Why. -> Creating the bigger picture to create a comprehensive understanding at every step in the process. // -> The Agent´s Self that can comprehend and execute, that can think autonomously to solve an objective. 


When humans conduct problem solving it can be dissected into a generalised approach:
1. Goal Identification: Identifying the objective or desired outcome.
2. Research & Information Gathering: Collecting relevant data and information.
3. Planning & Strategising: Creating a detailed plan of action.
4. Execution: Implementing the plan.
5. Monitoring & Adjustment: Evaluating progress, making necessary adjustments.
6. Reflection and Learning: Reviewing outcomes and gaining insights for future improvements.
Although its sequentially represented here, humans are capabale of jumping between the layers.

This framework aims to replicate the human approach to problem-solving through an artificial cognitive architecture designed to create AI employees that closely resemble human employees. Unlike other proposed architectures, this is intended to be a real-world implementation rather than a conceptual, theoretical framework.

The goal of this framework is to serve as the underlying structure for SoftGen.ai's Autonomous AI Developer and to lay the groundwork for creating other autonomous AIs. By creating a cognitive architecture that mimics a human software developer, we are paving the way for a general framework for autonomous cognitive entities capable of interacting with the world and solving objectives based on their environment and abilities.

The framework encompasses the environment in which the OACE operates, its practical abilities within the environment, its Long-Term & Short-Term (Working) Memory, and the core processing layers: 'Comprehension', 'Executive Function', 'Cognitive Control', and 'Task Prosecution'. These layers resemble a procedural system for problem-solving with guarded autonomy within each layer.

A sample flow:

0. The objective is discussed and defined outside of the OACE by the user. 
1. Comprehension Layer receives the objective from the user.
2. Comprehension Layer gains a deeper understanding of the objective, identifies relevant files/snippets, and devises strategies to achieve the objective. This involves thorough investigation and strategizing on how to approach the matter, making sense of the world using the Environmental Context.
3. Executive Function creates detailed implementation task plans to reach the objective. This involves creating detailed tasks.
4. Cognitive Control selects which task to work on from the plan.
5. Task Prosecution works on the task.
6. Cognitive Control evaluates task success/failure and decides what to do next. It may send the task back to prosecution or back to the Executive Function to replan.
7. Repeat until all tasks are completed.
8. Comprehension Layer receives information upwards after the Task List is completed, conducts further research, and may recommend additional testing, etc. This process is recursive until Comprehension Layer declares "Objective-reached".



## World / Environment
- The OACE operates within a Linux Docker container, essentially providing the AI with its own computer system. This setup allows the AI to utilize Linux as its personal navigation device to interact with the world, enabling a wide range of capabilities including file management, service configuration, server management, web browsing, package installation, and more. The Docker container also has the potential to interface with physical devices, allowing for diverse applications (for example connecting to camera feeds). For detailed information on the OACE's capabilities for the Autonomous AI Developer, refer to the Abilities section, which outlines its specific functionalities and limitations.

**Env Interaction Schema – sgconfig.json**
- The sgconfig.json file serves as a comprehensive configuration guide, detailing the operational blueprint for navigating and managing a project's directory structure and its nested folders. This file acts as a virtual onboarding manual for developers, outlining essential information such as the organization of the codebase, associated documentation, file storage conventions, general coding practices, local deployment procedures, and version control protocols with git. It functions as the definitive interaction schema for local development operations.
- Once integrated, the sgconfig World Environment Interaction schema is assimilated into the OACE's Long-Term Memory, subject to updates only upon modifications to the sgconfig.json file itself.
- Sgconfig.json is a file to be placed manually in any directory additional interaction schema is needed for context of operation. In our case that is the root directory of a codebase repo.


Sample Structure:
```json
{
  "projectInfo": {
    "name": "SoftGen.ai Web Interface",
    "description": "Next.js 13 Frontend Codebase for a Full Stack Web App Builder."
  },
  "file_types": {
    "FrontendPages": "Next.js pages directory for routing and view rendering.",
    "FrontendComponents": "Reusable React components for UI construction.",
    "FrontendHooks": "Custom React hooks for shared logic across components.",
    "FrontendApi": "Services for making API requests from the frontend.",
    "FrontendUtils": "Utility functions shared across frontend components."
  },
  "file_type_mapping": {
    "FrontendPages": {
      "path": "src/pages",
      "name": "FrontendPages"
    },
    "FrontendComponents": {
      "path": "src/components",
      "name": "FrontendComponents"
    },
    "FrontendHooks": {
      "path": "src/hooks",
      "name": "FrontendHooks"
    },
    "FrontendApi": {
      "path": "src/api",
      "name": "FrontendApi"
    },
    "FrontendUtils": {
      "path": "src/utilities",
      "name": "FrontendUtils"
    }
  },
  "file_type_imports": {
    "FrontendPages": ["@pages", "/pages"],
    "FrontendComponents": ["@components", "/components"],
    "FrontendApi": ["@api", "/api"],
    "FrontendHooks": ["@hooks", "/hooks"],
    "FrontendUtils": ["@utilities", "/utilities"]
  },
  "file_type_instructions": {
    "FrontendComponents": "Your objective is to craft sophisticated UI components using Chakra UI. Utilize Chakra UI for building user interfaces, leverage responsive styles feature of Chakra UI, use Chakra UI Icon library or React-icons, use Chakra UI's Flex and Grid for layouts, use Chakra UI's form components for user input, use Chakra UI's Link and Breadcrumb for navigation, use Chakra UI's Box as a base for custom components, list of available Chakra Components and Hooks for usage."
  },
  "localDeployment": {
    "prod": "npm install && npm run build && npm start",
    "dev": "npm install && npm run dev",
    "test": "npm run test"
  }
}
```


**Environmental State Reporting**:
- A contextualization report that details the latest interactions with the world.
- Maintains a log of events that describe changes to the world state, including edited files, opened files, opened browser tabs, browser interactions/inputs, etc...




## Abilities
These abilities are designed to facilitate the interaction of the OACE with the world environment. They are fixed procedures and flows that can be utilized in a flexible environment. They give all the magic tools to the OACE.

**Tools**: 
- CRUD Files
- Search File Snippets (semantic) in Folder and receive File & Lines (from-to)
- CRUD Terminal-Session
- CRUD Terminal-Commands in Session
- CRUD Browser Tab (Web browser interaction & automation)
- Read Web Browser Tab Log, Network, etc...
- Ask the user (If user input is needed it can be requested via tool, waits until it gets an answer)
- Websocket Testing
- Code Snippet Retrieval

**Procedures**
- Combination of tools to create a predefined procedure to interact with the world env & state. By chaining together tools we create a procedure that directly has a specialised use case (to not have to do the same combos over and over)
- Examples: Visit page and check for errors (server+browser) and return, run cURL request and return result, run Websocket Testing + send messages + check result, google/stack-overflow/etc… search + visit first 3 pages + report back, Read+Analyse+Evaluate Tab Log.


OACE Abilities Logic Preview:
![OACE Abilities Logic Preview](https://uploads-ssl.webflow.com/649081f0ae28305bdf0ff3b2/65c21c4b1ef3ac79eecd299a_preview-min.jpg)



## Memory
### Long-Term Memory (LTM)
**Episodic Memory**
- Records personal experiences and specific events
- Captures all activities and events associated with the OACE since its initiation. This includes periodic events and internal logs across all processes (individual Objectives that were aimed to be completed).

**Logging as Episodic Memory Source** 
- Every message (to Observe, Think or Act) produced by the LLM across the complete System (across all Layers) is logged. This is essentially every 'conscious' experience made.
- Each log entry is associated with Meta-data: Time, Process-ID, Layer-ID, Thread-ID, Type, Content
- Process-ID is associated with every Process created by the user. A Process is essentially the entire objective-based process of solving a defined objective and anything that occurs within it.
- Layer-ID indicates in which layer the logging has occurred (Comprehension, Executive Function, Cognitive Control, etc...)
- Thread-ID is the associated thread the message is a part of. In most cases, multiple messages (to Observe, Think or Act) are created within a Thread. The Thread represents a combination of multiple messages that form a list of associated events.
- Type: "Thread-Message", "Thread-Summary", "Thread-Output"
- Content is the actual content of the logged message.
- Currently, only the Thread-Summary is being used. All other types are being tracked for future use.

**Semantic Memory**
- Stores general knowledge and concepts
- Primarily consists of the LLM's trained Knowledge
- Also includes sgconfig related information for interaction with the environment, such as guidelines, documentation, and operational practices. This includes details about project structure and deployment strategies, encapsulated within World-Environment Interaction Schemas. These are also a fixed part of the general Knowledge as they are the instructions on how to navigate and use the project.
- Holds stable knowledge and beliefs about the world.
- This data is accessible for storage and retrieval.
- Future plans include learning by retraining (based on data from Episodic Memory and other sources)


### Working-Memory (WM) 
- The Working-Memory; Throughout all Layers, there is a persistent Layer of Memory that changes after every Layer-switch. This Layer encapsulates the broader and more detailed context – that describes everything that has happened, should happen, why its happening, where its happening.
- Constructs context with latest WM, received Layer Output, received Layer-Thread Summary

WM is primarily composed of the latest output layer info:
- Objective(s)
- Strategies 
- Current Task List (Latest task list that encapsulates the exact actions) and status
- Event Log of Layer-thread-summaries (all periodic events that happend since start of process)



Sample Structure:
```json
{
  "workingMemoryAsOf": "2024-02-06T15:00:00Z",
  "workingMemory": {
    "objectives": [
      {
        "id": "objective1",
        "description": "Describe the main goal of the current focus",
        "status": "in progress | completed | open"
      }
    ],
    "currentTaskList": [
      {
        "TaskID": "task1",
        "Type": "File",
        "File": {
          "FileName": "fileName.extension",
          "Type": "FrontendComponents, FrontendPages, etc....",
          "Instructions": " ... ",
          "FileDependencies": ["<file1.js>", "<file2.jsx>", "..."]
        },
        "contextRefs": ["ref1", "ref2", "..."]
      },
      {
        "TaskID": "task2",
        "Type": "Command",
        "Command": {
          "CommandString": "npm install package-name",
          "ExecutionPath": "/path/to/project/directory"
        },
        "contextRefs": ["ref3", "ref4", "..."]
      }
    ],
    "eventLog": [
      {
        "eventTime": "2024-02-06T12:00:00Z",
        "layer": "LayerName",
        "summary": "A brief summary of what occurred in this layer-thread",
      }
    ]
  }
}
```


## Layer Processing General:
- Each Layer functions as an independent OACE with its own set of abilities.
- CoT / ToT / Observe+Think+Act in each Layer.
- Each layer operates recursively or or up to a specified number of steps to generate a final output. It uses its abilities and internal dialogue to facilitate thinking. It operates within specified boundaries set by system-level instructions on the procedural general process to execute in each layer.

e## Layer Communication
- Bidirectional communication between each layer
- Utilizes a Top-to-bottom bus and Bottom-to-top communication bus.
- Upon creation of an output, the output and the layer-thread summary are shared in both directions. A latest Working Memory is also generated with the latest information.
- For top-to-bottom communication, this serves as an instruction for the next layer to be processed.
- For bottom-to-top communication, this provides information upon which the upper-layer can, but must not, Act upon and send down instructions again.


## Comprehension Layer
**Description:** 
The Comprehension Layer is the foundational stage where high-level strategies are formulated to achieve the set objective(s). It involves an in-depth analysis of the current environment, meaning existing files & code-snippets and their current state, then devising strategic plans to alter this state to meet the objectives. This layer acts as the brain's strategic center, conducting deep investigation and research to establish overarching goals and strategic directions.

**Input:** 
- Objective/Goal Definition: A articulation of the desired outcome or goal 

**Output:** 
- A comprehensive list of relevant resources such as folders, files, file snippets, etc., deemed crucial in the context of achieving the objective.
- A set of strategies designed to guide the process towards reaching the objective.

**Workflow/Processing:** 
1. **Goal Dissection:** The objective is broken down into various semantic topics that need to be addressed, identifying the key areas of focus.
2. **Mission Identification:** For each semantic topic, specific missions or tasks are defined that collectively contribute to achieving the overall goal.
3. **Asset Discovery:** This involves identifying and gathering relevant assets (e.g., folders, files, file snippets, server processes, web pages) that are pertinent to the missions.
4. **Strategy Formulation:** Crafting detailed strategies within the identified semantic topics to systematically approach the goals. This includes visiting and analyzing the identified assets to determine the necessary actions.


## Executive Function Layer
**Description:** 
The Executive Function Layer serves as the bridge between the high-level strategies devised in the Comprehension Layer and their execution. It is tasked with developing detailed, actionable plans by thoroughly defining each task, including potential contingencies and future considerations. This ensures a holistic approach towards achieving the set objectives. A key focus of this layer is on context retrieval, which guarantees that the plans are both appropriate and sufficiently detailed to align with the strategic direction, given the current context and environmental conditions.

**Input:** 
- Initial User Input
- Definition of Goals
- Defined Strategy to Achieve Goals
- Relevant Environmental Context (e.g., Files, Snippets)

**Output:** 
- A comprehensive implementation plan, presented as a task list, detailing the precise steps needed to fulfill the objective.
- The Task List includes context-specific details to facilitate precise execution.

**Workflow/Processing:** 
- Context Retrieval: Gathering relevant files, file snippets, folders, etc. (Refer to the OACE Abilities Logic Preview for the Code Snippet Retrieval Flow).
- Content Identification: Pinpointing relevant information within the retrieved context.
- Planning: Articulating the necessary changes in natural language.
- Task Breakdown: Segmenting the planned changes into individual tasks.
- Task Elaboration: Providing detailed instructions for each task, ensuring clarity on the required actions during execution.
- Contextual Reference Addition: Incorporating context references into tasks for enhanced specificity.



## Cognitive Control 
**Description:** 
The Cognitive Control layer is essential for determining immediate focus and guiding actions. It leverages cognitive functions like task selection, task switching, frustration management, and cognitive damping to make informed decisions. Cognitive damping is noteworthy for its role in internal deliberation, assessing the advantages and disadvantages of potential actions. This layer is responsible for prioritizing tasks by urgency and importance, initiating the creation of new tasks, and perpetually evaluating the current environment and outcomes of tasks.

**Input:** 
- Task List
- Latest Task Outputs

**Output:** 
- Task Execution Status
- Updates for the Executive Function (when necessary)

**Workflow/Processing:** 
- Receives the Task List and the most recent Task Outputs.
- Determines which tasks to initiate based on open status and absence of task outputs.
- Decides on the subsequent action to take.
- On successful task completion, proceeds to the next task.
- On task failure, evaluates whether to attempt the next task, retry the current task, or consult the Executive Function for reevaluation.
- Manages the execution of multiple tasks, taking into account task dependencies.



## Task Prosecution(s) Layer
**Description:** 
This layer is where the OACE interacts with its environment to execute the tasks defined by the Executive Function Layer. It involves the actual implementation of tasks, interacting with the environment using tools and procedures.

**Input:** 
- The task to be executed, and information on subsequent and previous tasks.

**Output:** 
- The outcome of the task execution, including success or error states, a summary of the task execution with references, and updates to the working memory (WM) based on the task outcomes.

**Workflow/Processing:** 
- The workflow and processing of the Task Prosecution layer vary based on the type of task. For example, if the task is a "File" type, it involves file changes. If it's a "Command" type, it's a command execution. Each task type has its own unique processing logic flow.

Sample Processing Flow:
![Sample Task Prosecution Flow](https://uploads-ssl.webflow.com/649081f0ae28305bdf0ff3b2/65c2383219ba2ff2abcd657e_TaskProsecutionFlow-min.jpg)






## Credits & additional resources
- This architecture is inspired by David Shapiro´s [ACE Framework](https://arxiv.org/pdf/2310.06775.pdf) 
- Draws also inspiration from CoALA ([CoALA](https://arxiv.org/pdf/2309.02427.pdf)) and the SOAR cognitive architecture 
- [Good introduction to understand cognitive architecture](https://www.youtube.com/watch?v=bfO4EkoGh40)
