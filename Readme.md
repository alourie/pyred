pyred - python library for connecting to Redmine [1] server
=============

pyred.py is a small python class that uses Redmine RESTAPI 
for talking and manipulating data on Redmine server.

Installation
------------

Just grab the redmine.py file and import it in your code.

Example:

cd /tmp
mkdir pyred
cd pyred
git clone show origin
touch __init__.py

Examples
------------

#!/usr/bin/python
from pyred.pyred import Redmine

url = 'https://redmine.example.org'
pass_file = 'pass_file'
# Test project
project_id = 20
# Test issue
issue_id =  251
# Test time entry
time_entry_id = 17

# Redmine generic object
r = Redmine(url=url,pass_file=pass_file)

# Get the Project given its id (or name)
#p = r.getProject(name=project_id)

# Get all issues of a given project
'''
criteria = {
    'project_id':project_id
}
is = r.getIssues(criteria=criteria)
print is
'''

# Update a given issue
'''
data = {'issue':{
                'subject':'Modified through Redmine API',
    },
}
response = r.updateIssue(issue_id,data)
print response
'''

# Create an issue on a given project
'''
data = {'issue':{
                'project_id':project_id,
                'subject':'Issue created via Redmine API',
                'priority_id': 4,
    },
}
print r.createIssue(data)
# If everything went ok -> <Response [201]>
# Otherwise -> <Response [404]>
'''

# Get Time Entry given its ID
'''
te = r.getTimeEntry(time_entry_id)
print te
'''

# Get all Time Entries of a given Issue
'''
data = {
    'issue_id':issue_id
}
tes = r.getTimeEntries(data)
print tes
'''

# Add Time Entry to a given Issue (or project)
'''
data = {'time_entry':{
                'issue_id':issue_id,
                'hours':'30m',
                'comments':'Time entry added via Redmine API',
                'activity_id':9,
    },
}
response = r.createTimeEntry(data)
print response
# If everything went ok -> <Response [201]>
# Otherwise -> <Response [422]>
'''

Credits
-------

- uses an awesome requests python library [2] by Kenneth Reitz

Contributors
------------

- Alex Lourie
- Sandro Bonazolla
- Javier Legido

References 
-----------
- [1] http://redmine.org
- [2] https://github.com/kennethreitz/requests
