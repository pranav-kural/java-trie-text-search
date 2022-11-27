# Tries Search
Utility program to do pattern or exact match search through catagorical data in less than linear time complexity.

## Usage

TriesSearch class will contain a Map of String and TrieNode for storing search data.

    Map<String, TrieNode> tries;

Each element inside this list represents one data object. 

Example:

If we're dealing with data of students, each element will represent data of one particular student. 

The String key of the map would represent UID, like student id, and the TrieNode structure will be built using **keywords** generated from the student's information.

When you perform a search, a list of student ids will be returned; these will the ids of students where a match for the query was found in students information (keywords stored in TrieNode).


    class StudentInfo {
        Map<String, Student> students = new HashMap<>();
        TriesSearch triesSearch = new TriesSearch();

        void addStudent(Student newStudent) {
          // store students information in map
          students.put(newStudent.getId(), newStudents);
          // update tries search data (add new student and the keywords of its information to search data set)
          triesSearch.addData(newStudent.getId(), newStudent.getKeywords());
        }

        // search for a query, return a list of students whose information has a match
        List<Student> searchStudent(String query) {
          // perform search and get list of matching students ids
          List<String> searchResult = this.triesSearch.pMatch(query);     // pMatch - pattern match, other option: eMatch - Exact Match
          // store resulting students
          List<Student> studentsWithMatch = new ArrayList<>(searchResult.size());   // size is known
          // get the students whose students ids are part of our search Result
          for (String studentId: searchResult) {
                // get the corresponding Student from our local map containing students and student ids and add to result list
                studentsWithMatch.add(this.students.get(studentId));
          }
          // return result
          return studentsWithMatch;
        }
    }

