# TaskConnect - Full-Stack Task Management System

A comprehensive full-stack application demonstrating advanced database design and backend development principles. Built with C# Windows Forms frontend and robust SQL Server backend, this system showcases complete database lifecycle management, complex relational data modeling, and enterprise-level data operations.

## Prerequisites

- **SQL Server** (Express or higher)
  - [Download SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
  - [Download SQL Server Express](https://www.microsoft.com/en-us/sql-server/sql-server-downloads#SQLServer)

- **SQL Server Management Studio (SSMS)**
  - [Download SSMS](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)

- **.NET SDK** (version 5.0 or higher)
  - [Download .NET SDK](https://dotnet.microsoft.com/download)

- **Visual Studio Code** or any preferred C# IDE
  - [Download VS Code](https://code.visualstudio.com/download)
  - Required Extensions for VS Code:
    - C# Dev Kit
    - .NET Core Tools

## Quick Setup

### 1. Database Setup
1. Open SSMS and connect to your SQL Server
2. Create database `TaskWorkerDB`
3. Execute `initial-schema.sql` from the `scheme` directory
4. **Keep SQL Server running during use**

### 2. Project Configuration
1. Clone/extract project to local machine
2. Update connection string in `Form1.cs` (line ~15):
   ```csharp
   "Server=YOUR_SERVER_NAME\\SQLEXPRESS;Database=TaskWorkerDB;Trusted_Connection=True;TrustServerCertificate=True;"
   ```
   **Replace YOUR_SERVER_NAME with your SQL Server instance name**
3. Build & run
```csharp
  dotnet restore
  dotnet build
  dotnet run
  ```

## Application Features

### Main Dashboard
- Choose between **Client** or **Worker** login/registration
- Clean, user-friendly interface with tabbed navigation

### Client Features

#### Client Profile Management
- **Register New Client**: Create a new client account with personal information
- **Login**: Access existing client account using client ID
- **Profile Update**: Modify name, phone, email, address, and payment information

#### Task Management
- **Browse Task Catalog**: View all available task types with descriptions and average fees
- **Request Tasks**: Submit task requests with:
  - Task type selection
  - Location preference
  - Time slot selection
  - Specific date and time preferences
- **View Task Requests**: Monitor all submitted requests with detailed status tracking
- **Rate Workers**: Provide ratings and feedback for completed tasks

#### Client Reports
- **Total Money Spent**: View complete spending history on completed tasks
- **Most Frequently Used Worker**: Identify your most assigned worker
- **Average Client Rating**: See your rating as received from workers

### Worker Features

#### Worker Profile Management
- **Register New Worker**: Create worker account with personal details
- **Login**: Access existing worker account using worker ID
- **Profile Configuration**: Set up availability including:
  - Specialties (Plumbing, Electrical, Cleaning, Painting, etc.)
  - Service locations (Downtown, Suburbs, etc.)
  - Available time slots

#### Task Assignment Management
- **View Assigned Tasks**: See all tasks assigned with complete details:
  - Task name and location
  - Fee information
  - Current status
  - Duration tracking
- **Task Status Updates**:
  - Mark tasks as "In Progress"
  - Mark tasks as "Completed"
  - Automatic duration calculation
- **Rate Clients**: Provide ratings and feedback for completed tasks

#### Worker Reports
- **Total Earnings**: Track total money earned from completed tasks
- **Task History**: View complete assignment history with ratings received

### Task Catalog Management
- **View All Tasks**: Browse available task types
- **Task Details**: See task descriptions, average fees, and estimated durations
- **Add New Tasks**: Create new task types (admin functionality)

### Advanced Features

#### Rating System
- **Bidirectional Ratings**: Both clients and workers can rate each other
- **Feedback System**: Detailed feedback collection
- **Rating Analytics**: Average rating calculations and display

#### Smart Task Assignment
- **Availability Matching**: Automatic worker filtering based on:
  - Required specialty
  - Location availability
  - Time slot availability
  - Current assignment status
- **Conflict Prevention**: Prevents double-booking of workers

#### Real-time Status Tracking
- **Task Request Lifecycle**: Open → Assigned → In Progress → Completed
- **Duration Tracking**: Automatic calculation of actual task duration
- **Timestamp Recording**: Complete audit trail of task progress

## Database Schema

The application uses a comprehensive database schema including:
- **Workers**: Worker profiles and contact information
- **Clients**: Client profiles and payment information
- **Tasks**: Task catalog with descriptions and fees
- **Specialties**: Worker skill categories
- **Locations**: Service areas
- **TimeSlots**: Available time periods
- **WorkerAvailability**: Junction table for worker schedules
- **TaskRequests**: Client task requests
- **TaskAssignments**: Worker task assignments
- **WorkerRatings**: Client ratings of workers
- **ClientRatings**: Worker ratings of clients

## Troubleshooting

### Connection Issues
- Verify your SQL Server instance name is correct
- Ensure SQL Server is running (check Services in Windows)
- If using Windows Authentication, make sure your Windows account has access to the database
- If firewall is blocking connections, allow SQL Server through the firewall

### Build Errors
- Make sure you have the correct .NET SDK version installed
- Try cleaning the solution: `dotnet clean` then `dotnet build`
- Verify all required packages are installed: `dotnet restore`

### Application Issues
- **Login Problems**: Ensure you're using the correct Client ID or Worker ID
- **No Available Workers**: Check that workers have set up their availability for the required specialty, location, and time slot
- **Task Assignment Issues**: Verify that the task request status allows for assignment

## Usage Tips

1. **For New Users**: Start by registering as either a client or worker
2. **Workers**: Complete your profile setup including specialties, locations, and time slots before expecting task assignments
3. **Clients**: Browse the task catalog first to understand available services and pricing
4. **Rating System**: Provide honest ratings and feedback to help improve the service quality
5. **Time Management**: Check available time slots before requesting tasks to ensure worker availability

## Technical Architecture

- **Frontend**: Windows Forms with C#
- **Backend**: C# with ADO.NET
- **Database**: Microsoft SQL Server
- **Architecture**: Layered architecture with separate service classes
- **Data Access**: Parameterized queries for security
- **Error Handling**: Comprehensive try-catch blocks with user-friendly error messages

## Need Help?

If you encounter any issues, please contact the development
