# testing
This repo is for testing purposes only. We are testing dev branch, testing for merge.

Here

else {
						vscode.window.showInformationMessage('Pushed successfully');
						// checkout to the testing branch
						git.fetch(remote, 'testing', function (err) {
							if (err) {
								console.log("error1:"+err);
								vscode.window.showErrorMessage(err);
							}
							else {
								git.checkout('testing', function (err) {
									if (err) {
										console.log("error2:"+err);
										vscode.window.showErrorMessage(err);
									}
									else {
										git.mergeFromTo(remote,'dev', function (err) {
											if (err) {
												console.log("error3:"+err);
												vscode.window.showErrorMessage(err);
											}
											else {
												git.push(remote, 'testing', function (err) {
													if (err) {
														console.log("error4:"+err);
														vscode.window.showErrorMessage(err);
													}
													else {
														vscode.window.showInformationMessage('Merged successfully');
													}
												});
											}
										});
									}
								});
							}
						});
					}