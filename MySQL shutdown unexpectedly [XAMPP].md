# MySQL shutdown unexpectedly [XAMPP]
Sometimes XAMPP-MySQL shows this type of Symptom below. I am showing some easy ways to resolve the issue.

## Issue/Symptom
<code style="color: red">6:40:45 PM  [mysql]  Error: MySQL shutdown unexpectedly.<br />
  6:40:45 PM  [mysql]  This may be due to a blocked port, missing dependencies,<br />
  6:40:45 PM  [mysql]  improper privileges, a crash, or a shutdown by another method.<br />
  6:40:45 PM  [mysql]  Press the Logs button to view error logs and check<br />
  6:40:45 PM  [mysql]  the Windows Event Viewer for more clues<br />
  6:40:45 PM  [mysql]  If you need more help, copy and post this<br />
  6:40:45 PM  [mysql]  entire log window on the forumsSolution:<br />
</code>

## Easy way to solve
1. Open shell from Xampp Control Panel and run:
```jsx
  mysqld --console --skip-grant-tables --skip-external-locking
```
2. Then again open an other shell and run:
```jsx
  mysqlcheck -r --databases mysql --use-frm
```
3. Now close both shells and restart the xampp.

## Another way to solve
1. Go to the Directory of `C:\xampp\mysql`
2. Make a zip file of the `data` folder
3. Go to `backup` folder and copy all the file without `ibdata1` and `ibtmp1` and then paste in the `data` folder.
4. Fully exit the `xampp` application from the PC.
5. Run the application again.
