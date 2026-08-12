# Should You List Every Tool on Your CV, or Only the Ones You Actually Know?
> Trọng Huy Dec (i have no idea who he is)

Last night, I was reviewing a fresher Data Engineer CV.

14 lines of tech stack.

Spark, Kafka, Airflow, dbt, Docker, BigQuery, Snowflake, Terraform, Great Expectations...

After reading it, I almost wanted to stand up and applaud.

If this had been me two years ago, I probably would have shaken my head and moved on.

"A fresher who knows this much probably only knows each tool superficially."

But last night, I didn't scroll past it.

I stopped.

I looked at that CV, then looked back at myself.

Because my CV used to look exactly like that.

I used to cram everything in.

I was afraid that if I removed even one tool, I would lose an opportunity.

I believed that listing more tools meant looking more impressive.

Then, during one interview, I was asked deep questions about Spark. I stumbled through them and couldn't properly answer anything about shuffle or partitioning.

That feeling stayed with me for years.

So today, I'm not writing this post to judge anyone.

I'm writing it because I understand.

Because every week, someone messages me asking:

"Should I list every tool on my CV if I only know the basics?"

The Trap Almost Everyone Falls Into

You build three personal projects.

Across those projects, you use Spark, Kafka, Airflow, dbt, Docker, and BigQuery.

Then the question pops into your head:

Should I list everything, or only the things I'm actually good at?

If you list everything, you're afraid you'll be asked deep questions and won't be able to answer.

If you list less, you're afraid your CV will look weak compared to everyone else's.

The truth is:

Both choices are wrong.

Because the right question isn't:

"Should I list it or leave it out?"

The right question is:

"How should I present it?"

I've reviewed more than 100 CVs from fresher and junior Data Engineers over the past two years.

And the clearest pattern I've seen is this:

The problem isn't the number of tools. The problem is how you communicate your level of understanding for each tool.

If you simply write "Spark" in your tech stack with no context, no project, and no explanation, the interviewer will naturally assume:

"This candidate is confident with Spark."

Then they ask deeper questions.

You can't answer.

And both sides waste their time.

That's not the interviewer's fault.

It's a communication problem created by the way you presented your CV.

Interviewers Don't Ask, "Do You Know X?"

I once interviewed a junior Data Engineer alongside a hiring manager.

There was one thing I realized very quickly:

Interviewers don't really care about how many tools you know.

They care about how deeply you understand the things you claim to know.

When you put "Spark" on your CV, an interviewer may reasonably expect you to be able to discuss things like:

Why did you use Spark instead of Pandas for that project?
How much data did you process?
How did you handle partitioning?
What problems did you encounter when running it?
How did you solve those problems?

You don't need to answer everything perfectly.

But you need to be able to explain your decisions thoughtfully.

I remember interviewing a fresher who listed BigQuery on their CV.

I asked:

"Which project did you use BigQuery for, and how much data did you process?"

They answered honestly:

"I used BigQuery for a personal project. The dataset was around a few hundred thousand rows. I chose it because of the free tier, and I wanted to learn SQL in a cloud environment."

That answer wasn't fancy.

But it was honest.

And it showed that the candidate understood where they actually stood.

I valued that much more than someone simply saying:

"I know BigQuery."

...and being unable to explain anything beyond that.

The 3-Level Framework: How to List Tools Without Digging Your Own Grave

This is the framework I use when reviewing CVs.

For every tool you know, ask yourself:

"Which level am I actually at with this tool?"

Level 1: Proficient

You're confident with it.

You use it frequently. You understand how to use it, when to use it, and the trade-offs involved.

If someone asks you deeper questions, you're comfortable discussing them.

For example:

You write SQL every day.

You understand window functions, CTEs, query optimization, and performance considerations.

How to list it:

Put it near the top of your CV, under your Core Skills or Technical Skills section.

These are the technologies interviewers are most likely to ask about first, and you're ready for it.

Before:

Tech Stack: SQL, Python, Spark, Kafka, Airflow, dbt, Docker, BigQuery

After:

Core Skills: SQL (PostgreSQL, query optimization), Python (Pandas, data pipeline scripting)

Level 2: Working Knowledge

You've actually used it in a project, even if it's a personal project.

You understand the main concepts.

You know how to set it up and get it running.

But if someone asks about internals, optimization, edge cases, or more advanced scenarios, you're not necessarily ready.

For example:

You used Airflow to orchestrate a pipeline.

You know how to write DAGs and trigger them.

But you've never dealt with complex retry strategies or built custom operators.

How to list it:

Put it in your Project Description, together with specific context.

Don't leave it sitting alone in the tech stack.

Give it a proper home.

Before:

Tech Stack: Airflow, Spark, Docker

After:

Built an ETL pipeline using Airflow for orchestration (5 DAGs, daily schedule). Processed data with PySpark on a local cluster (~2GB dataset). Containerized the pipeline with Docker for reproducibility.

See the difference?

It's the same set of tools.

But the second version tells the interviewer:

what you used,
how you used it,
how much you used it,
and in what context.
Level 3: Exposure

You've just started learning it.

Maybe you watched a course.

Maybe you read the documentation.

Maybe you followed a tutorial and got it working once.

You watched a Kafka course.

You read the Snowflake documentation.

You ran Terraform once.

There is absolutely nothing wrong with being at this stage.

Everyone has to start somewhere.

I did too.

I once put Kubernetes on my CV simply because I had successfully run:

kubectl get pods

...once.

I paid for that lack of honesty in an interview.

How to list it:

Don't put it in your main Tech Stack.

If you really want to mention it, put it lightly under something like Learning or Currently Exploring.

For example:

Currently Exploring: Kafka, Terraform, data quality frameworks

One small line.

But it communicates:

"I know this technology exists, and I'm learning it, but I'm not claiming to be proficient in it."

That's honesty.

And trust me, honesty is valued much more than you might think.

Before and After: A Real CV

Here's an example from a student I worked with, with their permission.

Before the Review

Technical Skills:

Python, SQL, Spark, Kafka, Airflow, dbt, Docker, BigQuery, Snowflake, Great Expectations, Terraform, Git

Project: E-commerce Data Pipeline

Built data pipeline
Used Spark, Kafka, Airflow
Stored data in BigQuery

I read it and couldn't tell what the candidate was actually good at.

Everything was listed.

But everything was vague.

After the Review

Core Skills:

Python (Pandas, scripting), SQL (PostgreSQL, window functions, query tuning)

Project: E-commerce Data Pipeline

Designed and implemented a batch ETL pipeline processing ~500K records/day from a REST API to BigQuery
Orchestrated the pipeline with Airflow (3 DAGs, error alerting via Slack webhook)
Transformed data using dbt (5 models, incremental materialization)
Containerized services with Docker Compose for local development

Currently Exploring:

Spark (completed Databricks learning path), Kafka (basic producer-consumer setup in personal lab)

Same person.

Same set of projects.

But the second CV tells a story.

An interviewer can immediately understand:

This candidate is confident with Python and SQL.
They have hands-on experience with Airflow and dbt through projects.
They're currently learning Spark and Kafka.

Clear.

Honest.

Easy to interview.

And being easy to interview is exactly what you want.

Because when the interviewer asks about something you actually know, you can answer well.

When you answer well, both sides win.

Less, But Deeper, Always Wins

I know what you're thinking.

"But the job description requires Spark, Kafka, and Airflow. If I don't list them, won't the ATS filter me out?"

That's a reasonable concern.

And I'm not going to pretend keyword matching doesn't exist.

It does.

But think about it this way:

If you put Spark in your Tech Stack just to pass the ATS, then reach the interview and can't answer a single question about Spark...

What's the result?

You pass the CV screening.

Then fail the technical interview.

And worse, you leave a bad impression.

The 3-level framework solves this.

You can still mention Spark, but put it in the right place:

in a project,
under Working Knowledge,
or under Currently Exploring.

The ATS still sees the keyword.

But the interviewer also understands the context.

I've seen hundreds of freshers worry that their CV doesn't have enough tools.

But after 50+ mock interviews, the pattern I've seen is clear:

I've never seen someone get rejected simply because their CV contained too few tools.

But I've seen plenty of people get rejected because they claimed to know a tool and couldn't explain it.

Less, but deeper.

That almost always wins.

What I Wish Someone Had Told Me Back Then

I remember my first CV.

It was packed with tools.

I was anxious.

I compared myself to everyone else and kept asking:

"Why does everyone else's CV have so many technologies? Am I doing enough?"

You're not alone.

Most of the freshers I've coached have had the same fear.

They're afraid their CV isn't impressive enough.

They're afraid removing a tool will cost them an opportunity.

They're afraid that being honest about their skill level will make them look weak.

But the opposite is often true.

When you're honest on your CV, you're giving yourself a major advantage in the interview.

Because you're more likely to be asked about things you're actually prepared to discuss.

Because you don't have to pretend.

Because you naturally speak with more confidence when you're talking about something you genuinely understand.

And interviewers notice that.

They always do.

I'm not telling you that your CV needs to be perfect.

I'm not telling you that you need to master everything before applying.

I'm simply saying this:

You don't need a perfect CV. You need an honest CV that shows you're serious about your journey.

List less.

Explain more.

And never be afraid to say:

"I'm currently learning this."

Because sometimes, that sentence makes a better impression than:

"I know this."
