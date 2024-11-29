//constructor
Task() = default;
Task(string n, string d, int p, int no)
    : name(n), deadline(d), priority(p), number(no) {}

//fungsi untuk menambah tugas
void addTask(){
    string name, deadline;
    int priority;

    cin.ignore();
    cout << "Enter Task Name: ";
    getline(cin, name);
    cout << "Enter Deadline (yyyy-mm-dd): ";
    cin >> deadline;
    cout << "Enter Priority : ";
    cin >> priority; cout <<endl;
    cout << "   1=Very Important" <<endl;
    cout << "   2=Important" <<endl;
    cout << "   3=Less Important" <<endl;

    // Validasi input
    if (priority < 1 || priority > 3) {
        cout << "Invalid input. Task not added.\\n";
        return;}

    int number = tasks.size()+1;
    tasks.push_back(Task(name, deadline, priority, number));
        cout << "Task added successfully!\\n";
    cout << left << setw(5)<<"No."<< setw(20) << "Name" << setw(15)
    << "Deadline" << setw(10)<< "Priority\\n";
    cout << string(50, '-') << endl;

    for (const auto &task : tasks) {
    cout << left <<setw(5)<<task.number<< setw(20) << task.name << setw(15) << task.deadline
    << setw(10) << task.priority << endl;}
void editTask() {
    displayTask();
    if (tasks.empty()) return;

    int no;
    cout << "Enter Task Number to Edit: ";
    cin >> no;

    auto it = find_if(tasks.begin(), tasks.end(), [no](const Task &task) {
        return task.number == no;
    });

    if (it != tasks.end()) {
        Task &t = *it;

        cin.ignore();
        cout << "Enter new name (current: " << t.name << "): ";
        getline(cin, t.name);
        cout << "Enter new deadline (current: " << t.deadline << "): ";
        cin >> t.deadline;
        cout << "Enter new priority (current: " << t.priority << "): ";
        cin >> t.priority;

        cout << "Task updated successfully!\\n";
    } else {
        cout << "Task not found.\\n";
    }
}

//fungsi untuk menghapus tugas berdasarkan nomor
void deleteTask() {
    if (tasks.empty()) {
        cout << "No tasks to delete.\\n";
        return;
    }

    displayTask();
    int no;
    cout << "Enter Task Number to Delete: ";
    cin >> no;

    auto it = find_if(tasks.begin(), tasks.end(), [no](const Task &task) {
        return task.number == no;
    });

    if (it != tasks.end()) {
        tasks.erase(it);
        cout << "Task deleted successfully!\\n";
    } else {
        cout << "Task not found.\\n";}
    for (const auto &task : tasks) {
    file << task.name << "|" << task.deadline << "|" << task.priority << endl;}

    cout << "Tasks saved successfully!\\n";
    cout << left << setw(5)<<"No."<< setw(20) << "Name" << setw(15)
    << "Deadline" << setw(10)<< "Priority\\n";
    cout << string(50, '-') << endl;

    for (const auto &task : tasks) {
    cout << left <<setw(5)<<task.number<< setw(20) << task.name << setw(15) << task.deadline
    << setw(10) << task.priority << endl;}
void editTask() {
    displayTask();
    if (tasks.empty()) return;

    int no;
    cout << "Enter Task Number to Edit: ";
    cin >> no;

    auto it = find_if(tasks.begin(), tasks.end(), [no](const Task &task) {
        return task.number == no;
    });

    if (it != tasks.end()) {
        Task &t = *it;

        cin.ignore();
        cout << "Enter new name (current: " << t.name << "): ";
        getline(cin, t.name);
        cout << "Enter new deadline (current: " << t.deadline << "): ";
        cin >> t.deadline;
        cout << "Enter new priority (current: " << t.priority << "): ";
        cin >> t.priority;

        cout << "Task updated successfully!\\n";
    } else {
        cout << "Task not found.\\n";
    }
}

//fungsi untuk menghapus tugas berdasarkan nomor
void deleteTask() {
    if (tasks.empty()) {
        cout << "No tasks to delete.\\n";
        return;
    }

    displayTask();
    int no;
    cout << "Enter Task Number to Delete: ";
    cin >> no;

    auto it = find_if(tasks.begin(), tasks.end(), [no](const Task &task) {
        return task.number == no;
    });

    if (it != tasks.end()) {
        tasks.erase(it);
        cout << "Task deleted successfully!\\n";
    } else {
        cout << "Task not found.\\n";}
    for (const auto &task : tasks) {
    file << task.name << "|" << task.deadline << "|" << task.priority << endl;}

    cout << "Tasks saved successfully!\\n";
    tasks.clear();
    string name, deadline;
    int priority;
    int number = 1;

    while (getline(file, name, '|') && getline(file, deadline, '|') && file >> priority) {
    file.ignore();
    tasks.push_back(Task(name, deadline, priority, number++));}
    cout << "Tasks loaded successfully!\\n";
}

void taskMenu(){
        char pil;
    do{
        do {
            cout <<"       Task"<<endl;
            cout <<"----------------------"<<endl;
            cout <<"a. Add Task"<<endl;
            cout <<"b. Display Task"<<endl;
            cout <<"c. Edit Task"<<endl;
            cout <<"d. Delete Task"<<endl;
            cout <<"e. Back To Menu"<<endl;
            cout <<"----------------------"<<endl;
            cout <<"Enter Your Choice : ";cin>>pil;


            // Periksa apakah input valid
            if (pil != 'a' && pil != 'b' && pil != 'c' && pil != 'd') {
            cout << "Invalid input! Please enter a valid option (a/b/c/d).\\n\\n";
            }

            }while (pil != 'a' && pil != 'b' && pil != 'c' && pil != 'd'); // Ulangi jika input tidak valid

            // Input valid, lakukan sesuatu berdasarkan pilihan
            switch (pil) {
                case 'a':
                    addTask();break;
                case 'b':
                    displayTask();break;
                case 'c':
                    editTask();break;
                case 'd':
                    deleteTask();break;
                case 'e':
                    cout << "returning to Main Menu...\\n";
                default:
                    cout<< "Invalid Choice! Try again.\\n";}

}while(pil != 'd');
saveTask();
